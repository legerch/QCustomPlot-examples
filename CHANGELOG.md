# Changelog

All notable changes to this project will be documented in this file.  
The format is based on [Keep a Changelog]

## [next]

## [2023_03_31]
### Changed
- Bump all applications examples to upstream version **2.1.1**
- Bump library **QCustomPlot-library** to [2.1.1.1](https://github.com/leger50/QCustomPlot-library/releases/tag/2.1.1.1)

## [2022_03_14]
### Changed
- Bump `QCustomPlot` library from _2.1.0.1_ to _2.1.0.2_

### Fixed
- Fix compilation issue with all examples, compilation definition `QCUSTOMPLOT_USE_LIBRARY` was missing

## [2022_01_10]

Creation of the repository containing multiples examples :
- Allow to build examples with **CMake**
- Add a `config.h.in` in order to track each version of each examples
- For all examples, replace include instructions `../../qcustomplot.h` by `qcustomplot.h`

<!-- Links -->
[keep a changelog]: https://keepachangelog.com/en/1.0.0/
[semantic versioning]: https://semver.org/spec/v2.0.0.html

<!-- Versions -->
[next]: https://github.com/leger50/QCustomPlot-examples/compare/2023_03_31...dev

[2023_03_31]: https://github.com/leger50/QCustomPlot-examples/compare/2022_03_14...2023_03_31
[2022_03_14]: https://github.com/leger50/QCustomPlot-examples/compare/2022_01_10...2022_03_14
[2022_01_10]: https://github.com/leger50/QCustomPlot-examples/releases/tag/2022_01_10