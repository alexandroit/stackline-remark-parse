# Upstream and maintenance review

Independent maintenance of `remark-parse@10.0.2` as `@stackline/remark-parse`.

- Source history: https://github.com/remarkjs/remark/tree/4178acc4c6ef7a1b95533c76dabd3de066c54160
- Original npm integrity: `sha512-3ydxgHa/ZQzG8LvC7jTXccARYDcRld3VfcgIIFs7bI6vbRSxJJmzgLEIIoYKyrfhaY+ujuWaf/PJiMZXoiCXgw==`.
- Issues checked: 2026-09-29T00:22:04.240592+00:00.
- Original authors, notices and license are retained. Published runtime and declaration file hashes are recorded in `.stackline/upstream.json`; reviewed differences are explicitly listed there.
- Original functional suites run against both source and the extracted final tarball. Type checks and the complete development/runtime audit must pass.

This maintenance branch selects the npm package from the upstream monorepo into the repository root and retains the upstream Git history. Shared tests are narrowed to this package and wired to its local implementation. Other monorepo products are not published by this repository.

## Issue triage

- https://github.com/remarkjs/remark/issues/1477: The reported trailing-hard-break roundtrip is not representable as a CommonMark hard break at the end of a block. CommonMark 0.31.2 section 6.7 requires a following inline. The parser semantics are preserved; this release does not promise lossless serialization of every hand-constructed AST. See https://spec.commonmark.org/0.31.2/#hard-line-breaks.

The evidence query fetched the latest 100 open and 30 closed issue/PR entries and removed PRs. This is a bounded review, not a claim of exhaustive issue history or resolution of every issue.

## Release verification

GitHub Actions publishes the reviewed passing-CI tarball. Release completion requires exact source identity, zero open CodeQL alerts, npm provenance and tarball identity, normal and aliased installs, and matching immutable GitHub release assets. Existing versions are never replaced.
