---
{"aliases":null,"tags":null,"description":null,"title":"dm_mod, Device Mapper Module","created":"2024-09-16T21:06:58","updated":"2024-09-16T21:14:51","dg-publish":true,"permalink":"/docs/dm_mod, Device Mapper Module/","dgPassFrontmatter":true}
---


> [!question] `modprobe dm_mod`라는 명령어를 쳤어. 이게 무슨 의미일까?

`modprobe dm_mod` 명령어는 리눅스 커널 모듈 중 하나인 **`dm_mod`**(Device Mapper 모듈)를 로드하는 명령입니다. 이 모듈은 LVM(Logical Volume Manager) 및 다른 디바이스 매핑과 관련된 기능을 제공하는 핵심적인 모듈입니다.

### 세부 설명

- **`modprobe`**: 이 명령은 커널 모듈을 로드하거나 언로드하는 데 사용됩니다. 모듈은 커널에 동적으로 추가하거나 제거할 수 있는 소프트웨어 컴포넌트로, 특정 하드웨어나 기능을 지원합니다.
  
- **`dm_mod`**: `dm_mod`는 **Device Mapper**의 줄임말로, 디바이스 맵핑과 관련된 모듈입니다. **Device Mapper**는 리눅스에서 물리적 디스크와 논리적 볼륨을 연결해주는 추상화 계층으로, LVM이나 소프트웨어 RAID 등을 지원하는 핵심 기능을 제공합니다. `dm_mod` 모듈은 LVM에서 물리적 볼륨을 논리적 볼륨으로 매핑하거나 암호화 디스크 관리, 스냅샷 기능 등을 사용할 때 필요합니다.

### `modprobe dm_mod`의 의미

이 명령은 **Device Mapper 모듈을 커널에 로드**하여 LVM을 포함한 다양한 장치 매핑 기능을 사용할 수 있도록 설정하는 역할을 합니다. 

- LVM을 사용하기 위해선 반드시 `dm_mod` 모듈이 로드되어 있어야 하므로, 리눅스 시스템에서 논리 볼륨 관리와 같은 기능을 사용할 때 이 모듈을 로드하게 됩니다.
  

### 상황에 따른 사용 예시

- **LVM 설정**: LVM을 설정하거나 사용할 때 `dm_mod` 모듈이 필요한데, 해당 모듈이 자동으로 로드되지 않았거나 수동으로 모듈을 로드해야 할 때 `modprobe dm_mod` 명령을 사용합니다.
  
- **암호화 디스크 설정**: `dm_mod`는 암호화된 볼륨을 사용하는 Device Mapper 기반의 기술에서도 사용되며, 이를 활성화하기 위해 모듈을 로드합니다.

### 요약

`modprobe dm_mod` 명령어는 LVM 및 디스크 매핑과 관련된 기능을 활성화하기 위해 **Device Mapper 모듈**을 커널에 로드하는 명령입니다. 이는 LVM을 사용하거나 논리 볼륨, 스냅샷, RAID, 암호화 볼륨 등을 다룰 때 필수적인 모듈입니다.

> [!question] 내가 알기로는 리눅스 커널은 모놀리식(monolithic)이라서 모듈화가 아니라고 들었는데 어떻게 된 일이지?

> [!quote] [[docs/리눅스 커널은 모놀리식이지만, 모듈화를 통하여 동적으로 기능을 추가하거나 제거할 수 있다\|리눅스 커널은 모놀리식이지만, 모듈화를 통하여 동적으로 기능을 추가하거나 제거할 수 있다]]