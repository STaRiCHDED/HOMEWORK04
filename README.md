[![Build Status](https://travis-ci.com/STaRiCHDED/Lab04.svg?branch=master)](https://travis-ci.com/STaRiCHDED/Lab04)
## HOMEWORK IV
### Tutorial
Вы продолжаете проходить стажировку в "Formatter Inc.
В прошлый раз ваше задание заключалось в настройке автоматизированной системы CMake.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в прошлый раз. Настройте сборочные процедуры на различных платформах:

-используйте TravisCI для сборки на операционной системе MacOS с использованием компиляторов gcc и clang;

Настройка git-репозитория hw04 для работы
```sh
$ export GITHUB_USERNAME=STaRiCHDED
$ export GITHUB_TOKEN=bc32bdc4ec6b0861e1d4607a812e278976be0fe9
$ cd ${GITHUB_USERNAME}/workspace
$  pushd .
$ source scripts/activate
$ git clone https://github.com/${GITHUB_USERNAME}/HOMEWORK03 projects/HOMEWORK04
$ cd projects/HOMEWORK04
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/HOMEWORK04
$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.10)
> project(formatter)
> set(CMAKE_CXX_STANDARD 11)
> set(CMAKE_CXX_STANDARD_REQUIRED ON)
> EOF
$ cat >> CMakeLists.txt <<EOF
> add_library(formatter STATIC formatter_lib/formatter.cpp)
> include_directories(formatter_lib)
> add_library(formatter_ex STATIC formatter_ex_lib/formatter_ex.cpp)
> include_directories(formatter_ex_lib)
> add_library(solver_lib STATIC solver_lib/solver.cpp)
> include_directories(solver_lib)
> EOF
$ cat >> CMakeLists.txt <<EOF
> add_executable(hello_world hello_world_application/hello_world.cpp)
> target_link_libraries(hello_world formatter formatter_ex)
> add_executable(solver solver_application/equation.cpp)
> target_link_libraries(solver formatter formatter_ex solver_lib)
> EOF
$ cat > .travis.yml <<EOF
> language: cpp
> EOF
$ cat >> script <<EOF
> cmake formatter_lib/CMakeLists.txt -Bformatter_lib/_build -DCMAKE_CURRENT_SOURCE_DIR=$PWD
> cmake --build formatter_lib/_build
> cmake formatter_ex_lib/CMakeLists.txt -Bformatter_ex_lib/_build -DCMAKE_CURRENT_SOURCE_DIR=$PWD
> cmake --build formatter_ex_lib/_build
> cmake hello_world_application/CMakeLists.txt -Bhello_world_application/_build -DCMAKE_CURRENT_SOURCE_DIR=$PWD
> cmake --build hello_world_application/_build
> cmake solver_application/CMakeLists.txt -Bsolver_application/_build -DCMAKE_CURRENT_SOURCE_DIR=$PWD
> cmake --build solver_application/_build
> EOF
$ cat >> .travis.yml <<EOF
> jobs:
>   include:
>   - name: "all projects"
>     script:
>     - cmake -H. -B_build
>     - cmake --build _build
>   - name: "each CMakeLists.txt"
>     script:
>     - source ./script
> EOF
$ cat >> .travis.yml <<EOF
> addons:
>   apt:
>     sources:
>       - george-edison55-precise-backports
>     packages:
>       - cmake
>       - cmake-data
> EOF
$ travis lint
$ ex -sc '1i|[![Build Status](https://travis-ci.com/STaRiCHDED/HOMEWORK04.svg?branch=master)](https://travis-ci.com/STaRiCHDED/HOMEWORK04)' -cx README.md
$ git add .
$ git commit -m"HW04"
$ git push origin master
```


## Links

- [Travis Client](https://github.com/travis-ci/travis.rb)
- [AppVeyour](https://www.appveyor.com/)
- [GitLab CI](https://about.gitlab.com/gitlab-ci/)
```
Copyright (c) 2015-2020 The ISC Authors
```
