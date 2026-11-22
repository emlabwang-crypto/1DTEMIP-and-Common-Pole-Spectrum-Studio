
# Supporting Codes for 3-D TEM Modeling With Induced Polarization

This repository contains two programs used in the constitutive tests and numerical validation of a three-dimensional (3-D) grounded-source transient electromagnetic (TEM) modeling study with induced polarization (IP). The programs address separate parts of the study: common-pole conductivity approximation and semianalytical reference responses for layered media. The full 3-D Maxwell–ADE–RCA forward solver is not included.

## Common Pole Spectrum Studio

Common Pole Spectrum Studio evaluates the frequency-dependent conductivity of the Debye, Cole–Cole, generalized effective medium theory of induced polarization (GEMTIP), and modified GEMTIP (MGEMTIP) models. A Fortran library evaluates the constitutive functions, while Python routines optimize shared positive relaxation rates and fit nonnegative spectral weights. Analytical relaxation poles are retained for Debye and MGEMTIP.

The graphical interface provides comparisons of constitutive spectra, poles, spectral weights, and approximation errors. Results can be exported as `phase_spectra.csv`, `pole_weights.csv`, `fit_summary.json`, and PNG or SVG figures. The fitting errors describe the constitutive approximation; they are not errors in the computed 3-D electromagnetic fields.

## 1D TEM–IP Studio

1D TEM–IP Studio computes transient electromagnetic responses from finite grounded-wire sources over horizontally layered polarizable media. It uses `empymod` for the layered-earth calculations and supports the conductivity models listed above. The program provides time-domain electric and magnetic field responses for ideal current shutoff, together with tools for comparison against externally computed responses.

These layered-earth results serve as independent reference solutions for checking the field responses of the 3-D numerical method, including signal decay and changes in polarity. The program is not a general 3-D electromagnetic solver.

## Installation

Python 3.12 is recommended. Run the commands from the directory of the corresponding program. Each package has its own `requirements.txt` and installation scripts.

**macOS**

```bash
bash setup_macos.sh
bash run_macos.sh
```

**Windows (Command Prompt)**

```bat
setup_windows.bat
run_windows.bat
```

Common Pole Spectrum Studio additionally requires `gfortran` to build its Fortran library. On Windows, a MinGW-w64 installation of `gfortran` must be available on `PATH`. See the README in each program directory for package-specific notes.

## Software dependencies and licensing

The `1DTEMIP/vendor` directory includes `empymod` and digital filter files. The corresponding third-party license notices are provided in `EMPYMOD_LICENSE.txt` and `LIBDLF_LICENSE.txt`. The repository license does not replace these notices.

## Citation

When using these programs in published work, cite the associated TEM–IP paper once its bibliographic details are available, together with any relevant third-party software references.
