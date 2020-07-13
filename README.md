# phpworld

A Cross-Technology Repository for version and compatibility tracking.

## Glossary

- Technology: the thing to be versionned and distributed. Examples: linux kernel, linux distribution, any language,
  framework, application, library, ...
- Distribution: a bunch of data representing the whole state of a versionned technology, from the releases to the
  lifecycle
- Release: a full version, optional based technologies, and optional lifecycle dates
- Lifecycle: optional dates incicating a release date, a date indicating the end of active support, a date indicating
  the end of security fixes meaning end of
  life
- Version: a valid version number grouping releases and represented from X, trough X.Y, to X.Y.Z-complement (see
  semantic versionning)
- Shortname: an optional nickname sur as Stretch, Bionic, Oopta, Daisy
- Stage: state of maturity of a version (eol, security, stable, testing, unstable)
- Based technologies: on what relies the technology (C Language for PHP, PHP for Symfony, Symfony for Akeneo PIM)
- Shipped technologies: describes what is embeded in the distributed technology (or defaults)
- Alternatives: If exists, list of other shipped or based technology distributions
- Long Term Support: does a particular version has a LTS extension for bug or security fixes

## Rationale

Distributed versions for PHP are like X.Y with releases like X.Y.Z
Distributed versions for linux have their own mecansim
How to choose what is above (frameworks, apps, libraries) and below (Operating Systems, ...) PHP versions ?
We would like to avoid glitches and gotchas on particular combinations.

`tool add technology version release [now]` i.e.: `tool add php 7.4 7.4.8 2020-07-09` updates or create `php.json`

```json
[{
  "version": "7.4",
  "last": {
    "version": "7.4.8",
    "released": "2020-07-09"
  }
}]
```

`tool set --stable technology version [now]` i.e.: `tool set --stable php 7.4 2021-11-28` updates or creates `php.json`

```json
[{
  "version": "7.4",
  "last": {
    "version": "7.4.8",
    "released": "2020-07-09"
  },
  "stable": "2021-11-28"
}]
```

`tool set` may have options like `--security`, `--eol`, `--stage`, `--lts`

`tool show [technology] [version]`
