# Governance

## Scope

This repository maintains the Home Assistant packaging, startup services,
Ingress proxy, authentication boundary, configuration, and documentation for
the Tautulli add-on. Tautulli application behavior is maintained by the
[upstream Tautulli project][upstream].

## Decision making

The repository maintainer has final responsibility for scope, security,
compatibility, releases, and merges. Decisions are informed by issue and pull
request discussion, test results, Home Assistant conventions, and upstream
Tautulli requirements.

Substantial or breaking proposals should be discussed in an issue before
implementation. Security-sensitive changes may be developed privately until a
coordinated disclosure is appropriate.

## Contributions and releases

Contributions are reviewed through pull requests. Accepted changes must pass
the repository checks and relevant image builds. Releases are prepared from the
default branch using semantic versioning, with release notes recorded in
`WHATSNEW.md`.

[upstream]: https://github.com/Tautulli/Tautulli
