---
{"dg-publish":true,"permalink":"/docs/Poetry/","title":"Poetry"}
---


## 2025-01-05 Poetry 2.0 버전 발표

[Announcing Poetry 2.0.0](https://python-poetry.org/blog/announcing-poetry-2.0.0)


Poetry 2.0.0에서는 `pyproject.toml` 파일 구조가 변경되어, 기존의 `[tool.poetry]` 섹션이 `[project]` 섹션으로 대체되었습니다. 이는 PEP 621을 준수하기 위한 것으로, `poetry check` 명령어를 통해 이전된 속성들을 확인하고 마이그레이션할 수 있습니다.

또한, Poetry 2.0.0에서는 다음과 같은 주요 변경 사항이 있습니다:

- **동적 필드 지원**: `version` 및 `readme`와 같은 필드를 동적으로 설정할 수 있도록 지원합니다. 이를 위해 `[project.dynamic]` 섹션에 해당 필드들을 추가해야 합니다.
- **향상된 의존성 해석기**: 의존성 해석 성능이 개선되어, 복잡한 의존성 트리도 더 빠르고 정확하게 처리할 수 있습니다.
- **환경 관리 개선**: 프로젝트별 가상 환경 관리가 개선되어, 격리된 환경에서의 작업이 더욱 원활해졌습니다.
- **설치 및 배포 프로세스 개선**: 패키지 설치 및 배포 과정이 최적화되어, 더 효율적이고 신뢰성 있게 패키지를 관리할 수 있습니다.

[[docs/Breaking Changes in Poetry 2.0.0\|Breaking Changes in Poetry 2.0.0]]

- **플러그인 시스템 도입**: 사용자가 Poetry의 기능을 확장할 수 있도록 플러그인 시스템이 도입되었습니다. 이를 통해 특정 요구 사항에 맞게 기능을 추가하거나 변경할 수 있습니다. [Using plugins](https://python-poetry.org/docs/plugins/#using-plugins) 문서를 참조하세요
	- `poetry export`와 `poetry shell`이 플러그인으로 격하되었습니다.

> PEP621이란?

[PEP 621](https://peps.python.org/pep-0621/?utm_source=chatgpt.com)은 Python 프로젝트의 핵심 메타데이터를 `pyproject.toml` 파일의 `[project]` 섹션에 표준화하여 정의하는 방법을 명시한 문서입니다.  이 표준은 패키징 관련 도구들이 일관되고 효율적으로 메타데이터를 처리할 수 있도록 돕습니다.

**주요 내용:**

- **정적 메타데이터 권장**: 프로젝트 이름(`name`), 버전(`version`), 설명(`description`) 등 핵심 메타데이터를 `pyproject.toml` 파일에 정적으로 정의하여 빌드 도구들이 이를 직접 활용할 수 있게 합니다.

- **동적 메타데이터 지원**: 일부 메타데이터는 동적으로 설정할 수 있으며, 이러한 경우 `dynamic` 필드에 해당 항목을 명시하여 도구들이 이를 인식하도록 합니다.

- **일관된 메타데이터 구조**: 여러 빌드 도구 간에 메타데이터 정의 방식을 통일하여 사용자들이 도구를 전환하거나 학습할 때 혼란을 줄이고, 빌드 도구 간 코드 공유를 촉진합니다.

이러한 표준화를 통해 Python 패키징 생태계의 일관성과 효율성이 향상되며, 사용자와 도구 개발자 모두에게 이점을 제공합니다. 

## poetry를 사용하여 가상환경 설정

```
## 폴더 생성
> mkdir oz-backend-django

## 폴더 이동
> cd oz-backend-django

## poetry 초기화
> poetry init

## poetry 의존성 설치 및 가상환경 세팅
> poetry install

## poetry 의존성 설치 및 가상환경 세팅 (poetry.lock파일 사용)
> poetry install --no-root

## 가상환경 접속하기
> poetry shell # lagacy
> poetry env activate # FROM 2.0.0
```

## CheetSheets

### Poetry 설치

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

또는 Homebrew를 사용:

```bash
brew install poetry
```

또는 pipx를 사용

```shell
pipx install poetry
```

### 새로운 프로젝트 생성

```bash
poetry new my-project
```

- `my-project`: 새로 생성할 프로젝트 디렉토리 이름

### 기존 프로젝트 초기화

```bash
poetry init
```

- 프로젝트에서 사용할 패키지 및 설정을 대화형으로 입력

### 가상 환경 활성화

```bash
poetry shell  # Deprecated
poetry env activate  # FROM 2.0.0
```

- Poetry가 관리하는 가상 환경을 활성화
- poetry env activate 명령은 가상 환경을 활성화하는 새로운 방식입니다.

### 의존성 추가

```bash
poetry add <패키지명>
```

- 예: `poetry add requests`
- 특정 버전 설치: `poetry add requests@^2.25.1`

### 개발 의존성 추가

```bash
poetry add --dev <패키지명>
```

- 예: `poetry add --dev pytest`

### 패키지 제거

```bash
poetry remove <패키지명>
```

- 예: `poetry remove requests`

### 의존성 설치

```bash
poetry install
```

- `pyproject.toml`에 정의된 모든 의존성을 설치

```shell
poetry install --no-root
```

- `poetry.lock`에 정의된 모든 의존성을 설치

[[docs/poetry.lock으로 설치하는 것과 pyproject.toml로 설치하는 것의 차이\|poetry.lock으로 설치하는 것과 pyproject.toml로 설치하는 것의 차이]]

### 의존성 업데이트

```bash
poetry update
```

- 모든 패키지를 최신 버전으로 업데이트. pyproject.toml, poetry.lock 모두 변경됨.

### 스크립트 실행

```bash
poetry run <명령어>
```

- 예: `poetry run python script.py`

### 패키지 버전 고정

```bash
poetry lock
```

- 현재 설정된 의존성 버전을 `poetry.lock` 파일에 고정

### 프로젝트 테스트

```bash
poetry run pytest
```

- pytest를 사용해 테스트 실행 (pytest는 미리 설치되어 있어야 함)

### 배포용 패키지 빌드

```bash
poetry build
```

- 배포 가능한 소스 배포본과 wheel 패키지를 생성

### PyPI에 배포

```bash
poetry publish
```

- PyPI에 패키지를 배포 (`~/.pypirc` 파일 설정 필요)

### 의존성 목록 보기

```bash
poetry show --tree
```

- 프로젝트의 모든 의존성을 트리 구조로 출력

### 가상 환경 관리

```bash
poetry env list
```

- Poetry가 관리하는 가상 환경 목록 보기

```bash
poetry env use <python 경로>
```

- 특정 Python 버전을 사용하도록 가상 환경 설정

### pyproject.toml 예시

```toml
[tool.poetry]
name = "my-project"
version = "0.1.0"
description = "A sample Python project"
authors = ["Your Name <you@example.com>"]

[tool.poetry.dependencies]
python = "^3.9"
requests = "^2.25.1"

[tool.poetry.dev-dependencies]
pytest = "^6.2.3"

[build-system]
requires = ["poetry-core>=1.0.0"]
build-backend = "poetry.core.masonry.api"
```

## poetry 설치 시 `.venv` 폴더가 프로젝트 내에 생성이 되지 않으시나요?

```python
poetry config virtualenvs.in-project true
poetry config virtualenvs.path "./.venv"
```
