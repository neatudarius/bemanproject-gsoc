---
title: Google Summer of Code 2026 Ideas List
---

## The Beman Project Ideas

Thank you for your interest in participating in [Google Summer of Code 2026 (GSoC26)](https://summerofcode.withgoogle.com/programs/2026)!

The Beman Project is a modern C++ libraries initiative: "Tomorrow's C++ Standard Libraries Today!"
It hosts implementations targeting current and upcoming C++ standards, including proposals for the C++ standard library and related tooling.
Contributing here means working on production-quality C++, standards alignment, and open source library development.

## Mentors of the projects

Mentors will be assigned when the project is initiated. Please feel free to reach out beforehand to discuss the project.

| Mentor | Email |
|--------|-------|
| [Darius Neațu](https://github.com/neatudarius) | neatudarius@gmail.com |
| [Dietmar Kühl](https://github.com/camio) | dietmar.kuehl@gmail.com |
| [Eddie Nolan](https://github.com/ednolan) | EddieJNolan@gmail.com |
| [Inbal Levi](https://github.com/inbal2l) | sinbal2lextra@gmail.com |
| [Jeff Garland](https://github.com/JeffGarland) | jeff@crystalclearsoftware.com |
| [Radu Nichita](https://github.com/RaduNichita) | radunichita99@gmail.com |

Below are a list of open projects for the Beman Project which can be developed as part of GSoC26.

---

### beman-tidy: Complete the tool and integrate it into Beman infrastructure

| | |
|-|-|
| **Difficulty** | 3/5 |
| **Project Size** | Variable (175 or 350 hours) |
| **Maximum instances** | 2 |
| **Constraints/requirements** | Python and C++; familiarity with CMake/build systems, CI (e.g. GitHub Actions), and the [Beman Standard](https://github.com/bemanproject/beman/blob/main/docs/beman_standard.md). |

#### Description

[beman-tidy](https://github.com/bemanproject/beman-tidy) is a tool aimed at The Beman Project contributors to check (`--dry-run`) and apply (`--fix-inplace`) the [Beman Standard](https://github.com/bemanproject/beman/blob/main/docs/beman_standard.md) to their repositories.

Only about 50% of the planned features are implemented today. The project has several phases:

1. **Complete the tool** - Implement the remaining features so that beman-tidy fully covers the Beman Standard.
2. **Validate on exemplar** - Run beman-tidy on the [exemplar](https://github.com/bemanproject/exemplar) project and fix any gaps (in the tool or in the standard).
3. **Run on all Beman libraries** - Apply beman-tidy across all [Beman libraries](https://bemanproject.org/libraries); fix issues and improve the tool as needed.
4. **Integrate into infrastructure** - Make beman-tidy part of the Beman Project infrastructure and run it on CI (e.g. GitHub Actions) on every pull request.

Success will give contributors a single, automated way to keep repositories aligned with the Beman Standard and will improve consistency across the project.

#### Reading & Related Material

* [beman-tidy](https://github.com/bemanproject/beman-tidy) ([PyPI](https://pypi.org/project/beman-tidy/))
* The [Beman Standard](https://github.com/bemanproject/beman/blob/main/docs/beman_standard.md) and the [Beman Library Maturity Model](https://github.com/bemanproject/beman/blob/main/docs/beman_library_maturity_model.md)
* [exemplar](https://github.com/bemanproject/exemplar) - Template library for new Beman libraries
* [Beman Project](https://bemanproject.org/) and [Beman libraries](https://bemanproject.org/libraries)

---

### Enhance std::execution (beman.execution & friends)

| | |
|-|-|
| **Difficulty** | 4/5 |
| **Project Size** | Large (350 hours) |
| **Maximum instances** | 2 |
| **Constraints/requirements** | strong C++ skills, familiarity with asynchronous programming, C++26 / P2300 sender–receiver model, and the [std::execution](https://wg21.link/p2300) specification. |

#### Description

[std::execution](https://wg21.link/p2300) is the vocabulary for asynchronous work in C++. [beman.execution](https://github.com/bemanproject/execution) is an implementation of this specification. The available tools currently specified are known to be incomplete. A project could create additional components to cover real-life use-cases. Some of the data structures and algorithms you implement could later be proposed for standardization.

The project could follow phases such as:

1. **Implement additional data structures** - A concurrent queue, a ring buffer, or similar building blocks for async pipelines.
2. **Implement missing algorithms** - Algorithms such as `when_any`, `sequence`, `repeat`, or refinements of existing algorithms in the execution model.
3. **Document, test, and align** - Ensure components are well-documented and tested, and align with the evolving std::execution design. Identify which components might be candidates for the C++ standard.
4. **Draft a standardization proposal for C++29** - Draft and submit a WG21 paper (or contribute to an existing one) proposing one or more of the implemented components for C++29.

Success will make beman.execution more usable for real-world async C++ code and will align it better with the evolving std::execution design; some of the work may feed into future standardization.

#### Reading & Related Material

* [beman.execution](https://github.com/bemanproject/execution), [beman.net](https://github.com/bemanproject/net), [beman.task](https://github.com/bemanproject/task).
* [P2300 std::execution](https://wg21.link/p2300) - C++ Working Draft model (soon to beC++26)
* [exemplar](https://github.com/bemanproject/exemplar) - Template library for new Beman libraries
* [Beman Project](https://bemanproject.org/) and [Beman libraries](https://bemanproject.org/libraries)

---

### Portable environment variables API (beman.env)

| | |
|-|-|
| **Difficulty** | 4/5 |
| **Project Size** | 450 hours |
| **Maximum instances** | 1 |
| **Constraints/requirements** | Strong C++ skills, familiarity with platform APIs (POSIX, Windows), and C++ Standardization process (or eager to learn). |

#### Description

There is no standard C++ portable API for manipulating environment variables. The standard provides only `std::getenv()` (from `<cstdlib>`) for reading; setting, unsetting, or enumerating variables relies on platform-specific APIs (`setenv`/`unsetenv` on POSIX, `SetEnvironmentVariable` on Windows), which are not portable. A portable API would benefit cross-platform applications, build tooling, and tests.

The project consists of:

1. **Implement a portable API - beman.env** - Design and implement a C++ library that provides a portable interface for getting, setting, unsetting, and enumerating environment variables across major platforms (e.g. Linux, macOS, Windows).
2. **Compare with well-known implementations** - Review and document how beman.env relates to existing solutions (e.g. [Boost.Process](https://www.boost.org/doc/libs/master/doc/html/boost/process/env.html) environment handling, platform-specific APIs). Identify gaps, design choices, and improvements to inform the API and the proposal.
3. **Test and verify on various environments** - Run the library on multiple platforms and toolchains; fix portability issues and document behavior and limitations.
4. **Draft a standardization proposal for C++29** - Write a WG21 paper (or contribute to an existing one) proposing a portable environment-variables API for the C++ standard (e.g. for C++29).

Success will give users a single, portable way to work with environment variables in C++ and will provide a concrete basis for a future `std::env` or similar facility.

#### Reading & Related Material

* [std::getenv](https://en.cppreference.com/w/cpp/utility/program/getenv) - Current standard API (read-only)
* [Boost.Process environment](https://www.boost.org/doc/libs/master/doc/html/boost/process/env.html) - Boost environment handling (e.g. for child processes)
* [exemplar](https://github.com/bemanproject/exemplar) - Template library for new Beman libraries
* [Beman Project](https://bemanproject.org/) and [Beman libraries](https://bemanproject.org/libraries)

---

