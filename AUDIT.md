# Repository Audit — `mkdocs-frontend-guide`

_Comprehensive content + infrastructure review. Generated 2026-06-30._

## What this project is

A personal frontend **learning guide** (React · TypeScript · planned Next.js) published as a
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) static site and deployed to
GitHub Pages via GitHub Actions (`mkdocs gh-deploy`). Content lives in `docs/` (~25,000 lines of
Markdown across `react/`, `reactapi/`, and `ts/`). Only ~67 files are git-tracked; the local
`venv/` is correctly ignored.

## Methodology

Every Markdown file was read in full and assessed for: content quality/depth, technical accuracy,
code-example correctness, completeness vs. the stated curriculum, internal consistency, and
concrete defects (broken links/images, placeholders, typos). Configuration, CI, navigation, and
assets were cross-checked against the filesystem.

## Overall assessment

**Grade: B-.** Strong breadth and several standout chapters, but three systemic problems:

1. **Version drift** — code and prose consistently lag one major version behind the libraries they
   teach (React Query v5, React 18/19, react-router v6, Zustand v5, axios v1, TS 5.x).
2. **Incompleteness** — four chapter files were empty; the Authentication chapter and the Forms
   "Testing" section were unfinished.
3. **Polish** — scattered placeholders, malformed markup, and typos.

The site structure, navigation (53/53 nav targets resolve), and deploy pipeline are sound and the
site builds.

---

## Findings

### A. Critical — code that is broken or wrong

| Location | Problem |
|---|---|
| `docs/reactapi/14.4`, `14.6`, `14.7`, `14.8` | Four chapter files were **0 bytes** but linked in nav → blank pages. |
| `docs/react/2.Setting Up the Environment.md` (~63) | Vite scaffold command missing the `--` separator → `--template react` ignored. |
| `docs/react/10.5.Redux Toolkit.md` (~559) | Selector reads `state.usersmodern.*` but store registers the reducer as `users` → selectors return `undefined`. |
| `docs/react/10.5.Redux Toolkit.md` (~835) | `handleChange` calls `preventDefault()` in `onChange` and writes `[e.target.email]: e.target.email` → `undefined: undefined`. |
| `docs/reactapi/14.2.0.Axios.md` (~150) | Misplaced brace/paren in a `.then(...)` → won't parse. |
| `docs/reactapi/14.3.Authentication.md` (~229) | `ProtectedRoute` checks `document.cookie.includes("token=")` while the chapter mandates **HttpOnly** cookies (invisible to JS) → example cannot work. |
| `docs/reactapi/14.2.1.Axios Industry Standards.md` (~1130) | Response interceptor returns `response.data` but consumers read `.data` again; also imports `getUser` which doesn't exist (`getUserById`). |
| `docs/reactapi/14.0.JSON Server.md` (~27, ~296) | `npx install …` is not a valid install command. |
| `docs/react/10.State Management in React.md` (~34) | Prose line sits inside a ` ```ts ` fence → breaks the snippet. |
| `docs/ts/3.Functions Objects and Classes.md` (~361) | `type Person` collides with `class Person` + `interface Person` → `TS2300`. |
| `docs/ts/11.5.React & Next.js Related TypeScript Types.md` (~82) | Lists `React.SubmitEvent<T>` — no such type (should be `React.FormEvent<HTMLFormElement>`). |

### B. Systemic — version drift (one major version behind)

- **React Query** — installs v5 but teaches removed v3/v4 APIs in `14.5.2`/`14.5.3`: `cacheTime`
  (→`gcTime`), two-arg `useMutation`, `keepPreviousData`, `suspense: true`, query-level
  `onSuccess/onError`, `<Hydrate>` (→`<HydrationBoundary>`), `idle`/`loading` status names. The
  files even contradict themselves between blocks.
- **React 18/19** — event pooling + `event.persist()` taught as current (removed in React 17);
  `defaultProps` on a function component; legacy `React.createElement` JSX transform with no mention
  of the automatic runtime; `forwardRef` shown as canonical (deprecated in React 19); `onKeyPress`.
- **react-router** — TOC/keywords reference v5 `Switch`/`useHistory`/`Redirect` and `useParams<T>()`
  even though chapter 9 itself uses v6/v7.
- **Zustand** — `shallow` as a selector second-arg (removed in v5; now `useShallow`).
- **axios v1** — interceptor typed `AxiosRequestConfig` (should be `InternalAxiosRequestConfig`);
  `ProgressEvent` (should be `AxiosProgressEvent`); MSW v1 `rest` import.
- **TypeScript** — legacy experimental decorators; deprecated `.eslintrc.js`; module resolution
  missing `node16`/`nodenext`/`bundler`.
- **Tooling** — CRA presented as the setup path; `@types/react-redux` install; PurgeCSS for Tailwind;
  Recoil listed as current (archived by Meta in 2025).

### C. Security mixed messages

The Authentication chapter correctly says *never use localStorage, prefer HttpOnly cookies*, but
both Axios files store the JWT in `localStorage` with no caveat, and the auth refresh interceptor
had no `_retry` guard (infinite loop on a failing `/refresh`).

### D. Completeness gaps

- `reactapi/`: four empty files; `14.3.Authentication` stopped at section 3 of a promised 13.
- `react/`: `8.React Forms` promised a "Testing Forms" section that didn't exist (numbering skipped
  13→15); empty `### Combining Reducers` heading in `7.React Hooks`.
- `ts/`: no stubs, but `5.Generics`, `12.Node`, `13.Advanced Topics`, `16.Troubleshooting` are thin;
  missing modern features (`satisfies`, `const` type params, assertion functions).

### E. Configuration / infrastructure

- `mkdocs.yml` — placeholder `site_url: https://stiename.example`; duplicate `pymdownx.superfences`
  entry.
- `.github/workflows/ci.yml` — pinned two packages by name and **ignored `requirements.txt`**; would
  break if any requirements-only plugin were enabled.
- `docs/index.md` — malformed email link (`https://…@gmail.com`, should be `mailto:`).
- Blog — only post was leftover Material-demo template (`…copy.md`) with placeholder contacts,
  duplicate image label, and an unterminated italic. `tags.md` empty; tags effectively unused.
- Assets — `reactguide.png` (1.7 MB) orphaned; `docs/assets/` totals ~10 MB (two GIFs at 3.8 MB and
  2.0 MB on one page) and should be optimized.

### F. Consistency / polish

Multiple heading conventions; inconsistent hook-import styles; mislabeled code fences; malformed
CriticMarkup in `React & Next Ecosystem.md`; split bold markers in `Important Keywords.md`; large
leftover HTML-comment outlines atop react chapters 1–6; recurring typos. Heavy duplication between
the two Axios files, the two React Query files, and within `ts/`.

---

## Remediation (this pass)

Addressed in the accompanying changeset:

- **Config/infra:** real `site_url`; removed duplicate `superfences`; `mailto:` email link; CI now
  installs from `requirements.txt`; removed orphaned `reactguide.png`; rewrote the template blog
  post into a real welcome post with the author's actual links.
- **react/, ts/, reactapi/:** applied the critical code fixes and the version-drift migrations listed
  above (React Query v5, React 18/19, react-router v6, Zustand v5, axios v1, TS 5.x).
- **Completeness:** authored the four empty `reactapi` chapters (Advanced API Scenarios, Real-Time
  Data, Security & Best Practices, File Handling), finished the Authentication chapter, and added the
  Forms "Testing" section.

## Still recommended (not done automatically)

- **Optimize images** — no image tooling is installed in this environment; compress/convert the
  `docs/assets/` PNGs/GIFs (consider WebP / optimized GIF) to cut ~10 MB of page weight.
- **Trim or adopt the unused plugins** in `requirements.txt` (minify, git-committers,
  git-revision-date, rss) — currently installed by CI but not enabled in `mkdocs.yml`.
- **Adopt tags** across real content, or remove the tags feature, since `tags.md`/tagging is largely
  unused.
- **Standardize** heading conventions and code-fence languages across files in a future style pass.
