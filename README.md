> [!NOTE]
> **9base status: Preserved** · **Lifecycle: archived reference copy.**
>
> This is a historical fork of [open-license-manager/licensecc](https://github.com/open-license-manager/licensecc).
> 9base retains it for provenance and reference and does not actively maintain it.
> Upstream source and inherited authorship remain attributed to their original contributors.

# licensecc — 9base preservation notes

## Role and provenance

This is a preserved upstream fork of the Open License Manager **licensecc**
C++ licensing library. Its upstream README documents the runtime library,
generator and companion examples. The existing
[.gitmodules](.gitmodules) points `extern/license-generator` to
`open-license-manager/lcc-license-generator`, not the 9base fork; the sibling
links below document related archives and do not rewrite dependency remotes.

The retained `develop` branch compared 0 commits ahead / 136 behind upstream
in the 8 October 2026 audit. No fork-only or account-linked Zaryob-authored
commits were exposed. This account check cannot exclude every unlinked
historical alias, but the inspected history does not establish a 9base
licensing product or current integration.

## Open License Manager / licensecc family

| Component | Preserved 9base repository |
| --- | --- |
| C++ licensing runtime library | [licensecc](https://github.com/9base/licensecc) |
| Project-key and license generator | [lcc-license-generator](https://github.com/9base/lcc-license-generator) |
| Precompiled build/test dependencies | [build-dependencies](https://github.com/9base/build-dependencies) |
| C++ integration examples | [examples](https://github.com/9base/examples) |

These are preserved upstream components. Their relationship is recorded by upstream
documentation; this curation does not assert a 9base licensing product or modify
submodule URLs. The existing upstream license and attribution remain unchanged.

## Historical note

These preservation notes were reconstructed on **8 October 2026** from the
repository tree, exposed branches, commit history and upstream comparisons.
They are new archival documentation, not evidence that this explanation existed
at the historical fork date. The original reason for retention or any deployment
is not established by the inspected record. No contemporary build, support or
upstream synchronization commitment is implied.

---

## Original upstream README (preserved)

# Licensecc

*Copy protection, licensing library and license generator for Windows and Linux.*

[![Standard](https://img.shields.io/badge/c%2B%2B-11-blue.svg)](https://en.wikipedia.org/wiki/C%2B%2B#Standardization)
[![unstable](http://badges.github.io/stability-badges/dist/unstable.svg)](http://github.com/badges/stability-badges)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
[![travis](https://travis-ci.org/open-license-manager/licensecc.svg?branch=develop)](https://travis-ci.org/open-license-manager/licensecc)
[![Github_CI](https://github.com/open-license-manager/licensecc/workflows/Github_CI/badge.svg)](https://github.com/open-license-manager/licensecc/actions)
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/81a1f6bc15014618934fc5fab4d3c206)](https://www.codacy.com/gh/open-license-manager/licensecc/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=open-license-manager/licensecc&amp;utm_campaign=Badge_Grade)
[![codecov](https://codecov.io/gh/open-license-manager/licensecc/branch/develop/graph/badge.svg?token=vdrBBzX6Rl)](https://codecov.io/gh/open-license-manager/licensecc)
[![Github Issues](https://img.shields.io/github/issues/open-license-manager/licensecc)](http://github.com/open-license-manager/licensecc/issues)

Protect the software you develop from unauthorized copies, limit the usage in time, to a specific set of 
machines, or prevent the usage in  virtualized environments. It is an open source license manager that helps to keep your 
software closed :smirk: . Among other features if it runs on a "real hardware" it can generate a signature of that hardware and report if the signature doesn't match.

A comprehensive [list of features](http://open-license-manager.github.io/licensecc/analysis/features.html), and their status is available in the project site. 

If you're experiencing problems, or you just need informations you can't find in the [documentation](http://open-license-manager.github.io/licensecc)  please contact us on [github discussions](https://github.com/open-license-manager/licensecc/discussions), we'll be happy to help. 

Remember to show your appreciation giving us a <a class="github-button" href="https://github.com/open-license-manager/licensecc" data-icon="octicon-star" aria-label="Star open-license-manager/licensecc on GitHub">star</a> here on GitHub.

## License
The project is donated to the community. It comes with freedom of use for everyone, and it always will be. 
It has a [BSD 3 clauses](https://opensource.org/licenses/BSD-3-Clause) licensing schema, that allows free modification and use in commercial software. 

## Project Structure
The software is made by 4 main sub-components:
-   a C++ library with a nice C api, `licensecc` with minimal (or no) external dependencies (the part you have to integrate in your software) that is the project you're currently in.
-   a license debugger `lcc-inspector` to be sent to the final customer when there are licensing problems or for calculating the pc hash before issuing the license.
-   a license generator (github project [lcc-license-generator](https://github.com/open-license-manager/lcc-license-generator)) `lccgen` for customizing the library and generate the licenses.
-   Usage [examples](https://github.com/open-license-manager/examples) to simplify the integration in your project.
 
## How to build
Below an overview of the basic build procedure, you can find detailed instructions for [Linux](http://open-license-manager.github.io/licensecc/development/Build-the-library.html) 
or [Windows](http://open-license-manager.github.io/licensecc/development/Build-the-library-windows.html) in the project web site. 

### Prerequisites
-   Operating system: Linux(Ubuntu, CentOS), Windows
-   compilers       : GCC (Linux) MINGW (Linux cross compile for Windows), MINGW or MSVC (Windows) 
-   tools           : cmake(>3.6), git, make/ninja(linux)
-   libs            : If target is Linux Openssl is required. Windows depends only on system libraries. Boost is necessary to build license generator and to run the tests but it's NOT a dependency of the final `licensecc` library. 

For a complete list of dependencies and supported environments see [the project website](http://open-license-manager.github.io/licensecc/development/Dependencies.html)

Clone the project. It has submodules, don't forget the `--recursive` option.

```console
git clone --recursive https://github.com/open-license-manager/licensecc.git
cd licensecc/build
```

### build on Linux

```console
cmake .. -DCMAKE_INSTALL_PREFIX=../install
make
make install
```

### build on Windows (with MSVC 2017)

```console
cmake .. -G "Visual Studio 15 2017 Win64" -DBOOST_ROOT="{Folder where boost is}" -DCMAKE_INSTALL_PREFIX=../install
cmake --build . --target install --config Release
```

### cross compile with MINGW on Linux

```console
x86_64-w64-mingw32.static-cmake .. -DCMAKE_INSTALL_PREFIX=../install
make
make install
```

## How to test

### on Linux

```console
make test
```

### on Windows (MSVC)

```console
ctest -C Release
```

## How to use

The [examples](https://github.com/open-license-manager/examples) repository that shows various ways to integrate `licensecc` into your project.

## How to contribute

The easiest way you can solve your problems or ask help is through the [discussions tab](https://github.com/open-license-manager/licensecc/discussions) above, otherwise if you think there is a problem you can open an issue in the [issue system](https://github.com/open-license-manager/licensecc/issues). 
Have a look to the [contribution guidelines](CONTRIBUTING.md) before reporting.
We use [GitFlow](https://datasift.github.io/gitflow/IntroducingGitFlow.html) (or at least a subset of it). 
Remember to install the gitflow git plugin and use `develop` as default branch for your pull requests. 
