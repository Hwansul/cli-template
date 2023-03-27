# 목차

- [목차](#목차)
- [Golang과 친해지기](#golang과-친해지기)
  - [의존성을 설치하는 방법](#의존성을-설치하는-방법)
    - [1. go 모듈 초기화하기](#1-go-모듈-초기화하기)
    - [2. 모듈(dependency) 설치하기](#2-모듈dependency-설치하기)
    - [3. 설치한 모듈을 사용하고자 하는 코드에 `import`하기](#3-설치한-모듈을-사용하고자-하는-코드에-import하기)
    - [4. `import`한 모듈을 원하는 코드 영역에서 사용하기](#4-import한-모듈을-원하는-코드-영역에서-사용하기)
    - [5. go mod tidy 명령으로 `go.mod` 파일과 `go.sum` 파일을 저장하기.](#5-go-mod-tidy-명령으로-gomod-파일과-gosum-파일을-저장하기)
  - [유용하고 강력한 기본 모듈](#유용하고-강력한-기본-모듈)
- [저장소 설정하기](#저장소-설정하기)
  - [포함된 모듈 목록](#포함된-모듈-목록)
  - [자동화](#자동화)

# Golang과 친해지기

## 의존성을 설치하는 방법

### 1. go 모듈 초기화하기

```shell
go mod init <module-name>
```

### 2. 모듈(dependency) 설치하기

```shell
go get github.com/user/package
```

- 설치 된 모듈은 `go.mod` 파일에 표시 됩니다.

### 3. 설치한 모듈을 사용하고자 하는 코드에 `import`하기

```go
import {
  "github/user/package"
}
```

### 4. `import`한 모듈을 원하는 코드 영역에서 사용하기

```go
func mai() {
  // Your code here
}
```

### 5. go mod tidy 명령으로 `go.mod` 파일과 `go.sum` 파일을 저장하기.

```shell
go mod tidy
```

## 유용하고 강력한 기본 모듈

- os/exec 모듈을 임포트 한 뒤 `exec.Command(name string, arg ...string) \*cmd` [명령어](https://pkg.go.dev/os/exec#Command)로 각 운영체제에 맞는 command line command를 사용 할 수 있어요.

```go
// (...)
func main () {
  cmd := exec.Command("tr", "a-z", "A-Z")     // 소문자를 대문자로 바꾸기
}
// (...)
```

# 저장소 설정하기

## 포함된 모듈 목록

|                           모듈                           |                       용도                       |
| :------------------------------------------------------: | :----------------------------------------------: |
| [Bubble Tea](https://github.com/charmbracelet/bubbletea) |   Functional 하고 Stateful한 터미널 앱 만들기    |
|  [Lip gloss](https://github.com/charmbracelet/lipgloss)  | 좋은 터미널 레이아웃을 구성하기 위한 스타일 정의 |

## 자동화

| 파일                             | 용도                                                                                                                                                                                                                     |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `.pre-commit-config.yaml`        | [pre-commit](https://pre-commit.com/) 설정 파일.<br/> `pre-commit install`로 git hook을 설치 할 수 있고, `pre-commit sample-config`로 이 파일을 생성 할 수 있습니다.                                                     |
| `.gorelaser.ymal`                | [GoReleaser](https://goreleaser.com/) 설정 파일. `goreleaser init` 명령어로 생성합니다. <br>컴파일, 릴리즈 노트 생성, Homebrew Formulae를 생성하고 나의 Homebrew Tap 저장소에 배포하는 작업을 자동화 하는 데 사용됩니다. |
| `.github/workflows/release.yml`. | Github Action을 이용해 [GoReleaser의 작업을 자동화](https://goreleaser.com/ci/actions/?h=github+ac) 하기 위한 설정 파일.                                                                                                 |
