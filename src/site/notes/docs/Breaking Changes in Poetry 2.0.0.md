---
{"aliases":null,"tags":null,"description":null,"links":null,"status":null,"title":"Breaking Changes in Poetry 2.0.0","created":"2025-01-07T21:13:09","updated":"2025-01-07T21:31:42","dg-publish":true,"permalink":"/docs/Breaking Changes in Poetry 2.0.0/","dgPassFrontmatter":true}
---


## Poetry 2.0.0의 Breaking Changes 요약

Poetry 2.0.0 릴리스에서는 기능 개선과 현대 표준에 맞춘 변경을 위해 여러 **Breaking Changes**와 제거된 기능이 도입되었습니다. 주요 변경 사항을 아래에 요약합니다.

---

### 1. **플러그인 전용 명령어**

- **`poetry export`**: 기본 Poetry 설치에 포함되지 않으며, 이제 별도로 설치해야 하는 `poetry-plugin-export` 플러그인을 통해 제공됩니다.
- **`poetry shell`**: 여러 문제로 인해 제거되었으며, 새로운 명령어인 `poetry env activate`로 대체되었습니다. 여전히 사용하고자 하는 경우, `poetry-plugin-shell` 플러그인을 설치해야 합니다.

---

### 2. **`poetry lock`의 기본 동작 변경**

- `poetry lock` 명령어는 이제 기본적으로 `--no-update` 옵션을 사용하여 잠금 파일(lock file)이 의도치 않게 업데이트되는 것을 방지합니다. 이전 기본 동작(잠금 파일 새로 생성)을 원할 경우, 명시적으로 `--regenerate` 옵션을 사용해야 합니다.

---

### 3. **`poetry add --optional`의 동작 변경**

- 선택적(optional) 의존성을 추가할 때, 이제 반드시 관련된 extra를 지정해야 합니다.

---

### 4. **디렉토리 전환(`--directory/-C`)의 동작 변경**

- `--directory/-C` 옵션은 이제 프로젝트 루트만 설정하는 대신 실제 작업 디렉토리를 전환합니다. 이전 동작은 새로운 옵션인 `--project/-P`를 통해 사용할 수 있습니다.

---

### 5. **`tool.poetry.include`의 일관된 동작**

- `tool.poetry.include`를 사용할 때 기본 형식이 이제 모든 경우에 "sdist 전용"으로 통일되었습니다. 이전에는 디렉토리에는 "sdist 전용", 파일에는 "sdist와 wheel"이 기본값이었습니다.

---

### 6. **설정 변경**

- 설정 값 `experimental.system-git-client`가 `system-git-client`로 이름이 변경되었습니다.
- 설정 값 `virtualenvs.prefer-active-python`이 반대 의미를 가진 `virtualenvs.use-poetry-python`으로 대체되었습니다. 기본 동작도 이에 따라 변경되었습니다.

---

### 7. **Deprecated 및 제거된 기능**

- `pyproject.toml` 파일에서 `[tool.poetry]` 섹션의 더 이상 사용되지 않는 필드들이 `[project]` 섹션의 대응 필드로 완전히 대체되었습니다.
- Python 3.8 지원이 중단되었습니다.
- Poetry 1.1 이전 버전에서 생성된 잠금 파일(lock file)은 더 이상 지원되지 않습니다.
- pip 기반 설치 방법(`installer.modern-installation = false`)이 제거되었습니다.
- 기본적으로 setuptools를 제외했던 설정 옵션 `virtualenvs.options.no-setuptools`가 제거되었습니다.

---

이러한 변경 사항은 Poetry의 기능을 크게 발전시키며, 플러그인 및 업데이트된 워크플로우 채택을 장려하고 더 이상 사용되지 않는 기능과 동작을 단계적으로 제거하기 위한 목적을 가지고 있습니다.

---

## Q. `tool.poetry.dependencies` 섹션은 어디로 가야 하는가?

Poetry 2.0.0에서는 `tool.poetry.dependencies`에 정의된 의존성을 리팩터링하는 방법이 변경되었습니다. 아래는 이를 처리하는 방법에 대한 요약입니다.

### **1. 기본 리팩터링: `project.dependencies`로 이동**

- **사용 조건**: Poetry 고유의 기능이 필요하지 않은 경우.
- 기존의 `tool.poetry.dependencies` 섹션을 **`project.dependencies`** 로 옮깁니다.
- 예를 들어, 아래와 같은 기존 설정:

```toml
[tool.poetry.dependencies]
requests = "^2.28"
```

이를 다음과 같이 변경합니다:

```toml
[project.dependencies]
requests = "^2.28"
```

[Dependency groups](https://python-poetry.org/docs/managing-dependencies#dependency-groups): poetry는 기본적으로 `[project.dependencies]`에 정의된 의존성들을 암묵적으로 `main` 그룹으로 간주합니다.

---

### **2. Poetry 고유 기능 사용 시: 병행 사용**

- **사용 조건**: Poetry에서만 지원하는 특정 기능(예: 추가 메타데이터)이 필요한 경우.
- 이 경우, 표준 의존성은 `project.dependencies`에 정의하고, Poetry 고유 설정은 `tool.poetry.dependencies`에 추가적으로 정의합니다.
- 예시:

```toml
[project.dependencies]
requests = "^2.28"

[tool.poetry.dependencies]
requests = { version = "^2.28", extras = ["security"] }
```

---

### **3. 완전한 의존성 동적 선언**

- **사용 조건**: 프로젝트가 Poetry 고유의 기능을 광범위하게 사용하는 경우.
- `project.dependencies`를 **동적(dynamic)**으로 선언하고, 모든 의존성을 `tool.poetry.dependencies`에 유지합니다.
- 예시:

```toml
[project]
dependencies = ["dynamic"]

[tool.poetry.dependencies]
requests = "^2.28"
```

---

### **4. Deprecated 필드 확인**

- Poetry 2.0에서는 일부 필드가 더 이상 지원되지 않으므로, 다음 명령어를 사용하여 확인 및 수정합니다:

```bash
poetry check
```

이 명령어는 `pyproject.toml` 파일에서 더 이상 사용되지 않는 필드와 대체 항목을 알려줍니다[1].

---

### **5. 리팩터링 후 검증**

- 리팩터링 후, 의존성 설치 및 잠금 파일 업데이트를 통해 설정이 올바르게 작동하는지 확인합니다:

```bash
poetry install
poetry lock --check
```

---

이와 같은 접근 방식을 통해 기존의 `tool.poetry.dependencies` 설정을 최신 표준과 호환되게 리팩터링할 수 있습니다.

## Q. 그러면 `tool.poetry.group.*`는 어떻게 되는가?

<https://python-poetry.org/docs/managing-dependencies#dependency-groups>

그대로 사용하면 된다. 예를 들면..

```toml
[tool.poetry.group.test.dependencies]
pytest = "^6.0.0"
pytest-mock = "*"
```

따라서 이 의존성들은 poetry에 의해서 관리되기 때문에 배포환경에선 설치되지 않는다. 추후 PyPI에 퍼블리싱해도 의존성에 나타나지 않게된다.

Poetry 2.0.0에서는 기존에 사용하던 `tool.poetry.group.dev.dependencies` 섹션이 그대로 유지됩니다. 따라서 별도의 이동이나 리팩터링이 필요하지 않습니다. 개발 의존성은 여전히 **dependency groups** 기능을 통해 관리되며, `tool.poetry.group.dev.dependencies`는 그대로 사용 가능합니다.

---

### **Dependency Groups 유지 및 활용**

1. **기존 구조**: 아래와 같은 구조는 여전히 유효합니다.

   ```toml
   [tool.poetry.group.dev.dependencies]
   pytest = "^7.1.2"
   pytest-cov = "^3.0"
   ```

2. **설치 명령어**:
   - 개발 의존성만 포함하여 설치하려면 다음 명령어를 사용합니다:

     ```bash
     poetry install --with dev
     ```

   - 개발 의존성을 제외하고 설치하려면:

     ```bash
     poetry install --without dev
     ```

3. **새로운 그룹 추가**:
   - 새로운 그룹을 추가하려면 `-G` 옵션을 사용합니다:

     ```bash
     poetry add <패키지명> -G <그룹명>
     ```

   - 예를 들어, 테스트 그룹에 `pytest`를 추가하려면:

     ```bash
     poetry add pytest -G test
     ```

---

### **Poetry 2.0에서의 변화**

Poetry 2.0에서도 dependency groups는 동일한 방식으로 지원됩니다. 따라서 `tool.poetry.group.dev.dependencies` 섹션은 유지되며, 개발 의존성을 명확히 구분하여 관리할 수 있습니다[1][3][4].

---

### **검증**

리팩터링 후 또는 새로운 그룹 설정 후에는 아래 명령어로 설정이 올바른지 확인하세요:

```bash
poetry check
poetry lock --check
```

결론적으로, `tool.poetry.group.dev.dependencies`는 변경 없이 그대로 사용하면 됩니다.
