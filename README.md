# 목차

- [목차](#목차)
  - [Go 의존성을 설치하는 방법](#go-의존성을-설치하는-방법)
    - [1. go 모듈 초기화하기](#1-go-모듈-초기화하기)
    - [2. 모듈(dependency) 설치하기](#2-모듈dependency-설치하기)
    - [3. 설치한 모듈을 사용하고자 하는 코드에 `import`하기](#3-설치한-모듈을-사용하고자-하는-코드에-import하기)
    - [4. `import`한 모듈을 원하는 코드 영역에서 사용하기](#4-import한-모듈을-원하는-코드-영역에서-사용하기)
    - [5. go mod tidy 명령으로 `go.mod` 파일과 `go.sum` 파일을 저장하기.](#5-go-mod-tidy-명령으로-gomod-파일과-gosum-파일을-저장하기)
  - [포함된 모듈 목록](#포함된-모듈-목록)
  - [자동화](#자동화)
- [TODOS](#todos)

## Go 의존성을 설치하는 방법

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

## 포함된 모듈 목록

|                           모듈                           |                       용도                       |
| :------------------------------------------------------: | :----------------------------------------------: |
| [Bubble Tea](https://github.com/charmbracelet/bubbletea) |   Functional 하고 Stateful한 터미널 앱 만들기    |
|  [Lip gloss](https://github.com/charmbracelet/lipgloss)  | 좋은 터미널 레이아웃을 구성하기 위한 스타일 정의 |

## 자동화

| 파일                             | 용도                                                                                                                                                                                                                     |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `.gorelaser.ymal`                | [GoReleaser](https://goreleaser.com/) 설정 파일. `goreleaser init` 명령어로 생성합니다. <br>컴파일, 릴리즈 노트 생성, Homebrew Formulae를 생성하고 나의 Homebrew Tap 저장소에 배포하는 작업을 자동화 하는 데 사용됩니다. |
| `.github/workflows/release.yml`. | Github Action을 이용해 [GoReleaser의 작업을 자동화](https://goreleaser.com/ci/actions/?h=github+ac) 하기 위한 설정 파일.                                                                                                 |

# TODOS

- 쉘 스크립트 임베딩용 모듈 설치해두고 문서화 해 두기.
