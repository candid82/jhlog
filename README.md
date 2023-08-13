# jhlog

jhlog is a [Joker](https://github.com/candid82/joker) script that generates release notes based on git history and GitHub pull requests. It requires Joker v1.3 or later.

## Usage

### As a CLI tool

```
./jhlog.joke --path <path to git repo> --first <sha or tag of first commit> [--last <sha or tag of last commit>] [--github-token <github-token>]
```

For example:

```
> ./jhlog.joke --path ~/joker --first v1.1.0 --last v1.2.0
- [#487](https://github.com/candid82/joker/pull/487) - Add control over markdown rendering options ([@wnh](https://github.com/wnh))
- [#486](https://github.com/candid82/joker/pull/486) - Bump golang.org/x/sys from 0.0.0-20200302150141-5c8b2ff67527 to 0.1.0 ([@dependabot](https://github.com/apps/dependabot))
- [4ae629c](https://github.com/candid82/joker/commit/4ae629c5fd17a968de7c54b802e6ef8faf2522dd) - v1.2.0 (Roman Bataev)
- [d6274af](https://github.com/candid82/joker/commit/d6274afc8d757eaaaf15447328cc721fc78a8584) - Add test for linting binding types. (Roman Bataev)
- [a50e8da](https://github.com/candid82/joker/commit/a50e8da79039c7b7a0cdd9a2722aa872e99bd584) - [linter] Infer types for bindings. (Roman Bataev)
- [9f739a7](https://github.com/candid82/joker/commit/9f739a7d7ce826cc6ea20b8f7fe71aadc4be19e8) - Update yaml to v2.4.0. (Roman Bataev)
- [8a8c8b8](https://github.com/candid82/joker/commit/8a8c8b8477c8ff7e3ae1b3fca55bd38060fa917f) - Update readme. (Roman Bataev)
- [6515d55](https://github.com/candid82/joker/commit/6515d551224b46aa6e50cc91f4d2eac5e986b9a8) - Update readme. (Roman Bataev)
```

If GitHub token is not provided as an argument, `jhlog` will try to read `~/.jhlog` file which should contain GitHub host => token dictionary in [TOML](https://toml.io/en/) format, e.g.:

```
github-enterprise.foo.com = "<token>"
github.com = "<token>"
```

### As a library

```
(ns-sources
  "jhlog" {:url ".../jhlog"}})

(ns foo
  (:require [jhlog]))

(jhlog/change-log-notes "path/to/git/repo" "v1.0" "v1.1" "github-token")
```
