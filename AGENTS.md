# AGENTS.md

legend-pure-next is a fork of a FINOS project (finos/legend-pure-next) used for a delegated, supervised framework-upgrade demo. The default branch is pinned to upstream `e81166963b1b`; never sync it with upstream and never push to it directly — every change goes through a **draft pull request**.

## Toolchain
- JDK 25 (Temurin) for `bootstrap/`; Maven 3.9; `just`

## Build
```
cd bootstrap/legend-pure-next-bootstrap && mvn -q -DskipTests install
```

## Test
```
cd bootstrap/legend-pure-next-bootstrap && mvn -q test
```

**Note:** this repo is not a single Maven reactor. The Java-direct backend lives in `bootstrap/legend-pure-next-bootstrap` and its pom sets `maven.compiler.release` **25**, so building it needs a JDK 25 (the repo is driven by `just`; see `Justfile` and `bootstrap/Justfile`).

## Rules
- Never edit anything under `.github/workflows/` (release/docker/publish workflows were intentionally removed in this fork).
- Never delete, `@Ignore`, or weaken tests to get a build green; document irreducible failures in the PR body instead.
- Touch only `pom.xml`, `CHANGELOG.md`, and the `src` files an upgrade requires.
