# ros2-pkg-template
This is the template repository for the ROS 2 package with [Industrial CI](https://github.com/ros-industrial/industrial_ci).
## Before use
Adjust the `ROS_DISTRO` tag in [ci.yml](https://github.com/Alpaca-zip/ros2-pkg-template/blob/main/.github/workflows/ci.yml) to suit your ROS 2 environment:
```yaml
jobs:
  clang_format_check:
    runs-on: ubuntu-latest
    steps:
      - name: checkout
        uses: actions/checkout@v2
        with:
          ref: ${{ github.head_ref }}
      - name: run industrial_ci
        uses: 'ros-industrial/industrial_ci@master'
        env:
          ROS_DISTRO: humble # Replace humble for your chosen distro.
          CLANG_FORMAT_CHECK: file
          CLANG_FORMAT_VERSION: "14"
```
## Industrial CI
This template provides a comprehensive CI pipeline for ROS 2 project using GitHub Actions and the ros-industrial/industrial_ci action.
- `Clang Format Check` : Ensures code formatting adheres to defined standards using [clang-format](https://clang.llvm.org/docs/ClangFormat.html).
- `Clang Tidy Check` : Validates code for potential issues and adherence to coding standards using [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/).
- `Black Check` : Ensures code formatting adheres to PEP standards using [Black](https://black.readthedocs.io/en/stable/).
- `Pylint Check` : Runs [Pylint](https://pylint.readthedocs.io/en/stable/) for static code analysis on Python code.
- `Build Check` : Performs a build for both main and testing ROS 2 repositories to ensure the codebase builds correctly.
## To pass all checks...
### clang-format
**1. install**
```
$ sudo apt-get install clang-format
```
**2. Format with clang-format**
```
$ cd <path_to_this_package>
$ find . -type f \( -name "*.cpp" -or -name "*.hpp" -or -name "*.h" \) -exec clang-format -i -style=file {} \;
```
### Clang-Tidy
**1. install**
```
$ sudo apt-get install clang clang-tidy
```
**2. Format with Clang-Tidy**
```
$ cd <path_to_your_workspace> && colcon build --packages-select <this_package> --cmake-args -DCMAKE_EXPORT_COMPILE_COMMANDS=1
$ clang-tidy -p build/<this_package>/ <path_to_this_package>/src/<your_cpp> -fix
```
### Black
**1. install**
```
$ pip install black
```
**2. Format with Black**
```
$ cd <path_to_this_package>
$ find . -type f -name "*.py" -exec black {} \;
```
### Pylint
**1. install**
```
$ pip install pylint
```
**2. Run Pylint**
```
$ cd <path_to_this_package>
$ find . -type f -name "*.py" -exec pylint {} \;
```
