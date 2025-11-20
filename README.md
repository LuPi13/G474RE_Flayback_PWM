# STM32G474RE Flyback PWM 프로젝트

STM32G474RE 마이크로컨트롤러를 사용한 Flyback PWM 제어 프로젝트입니다.

## 개발 환경 요구사항

- **STM32CubeIDE** (v1.x 이상 권장)
- **STM32CubeMX** (프로젝트 재구성이 필요한 경우)
- **ARM GCC 툴체인** (STM32CubeIDE에 포함)

## 프로젝트 클론 및 빌드 방법

### 1. 저장소 클론

```bash
git clone <repository-url>
cd G474RE_Flayback_PWM
```

### 2. STM32CubeIDE에서 프로젝트 임포트

1. STM32CubeIDE 실행
2. **File** → **Open Projects from File System...**
3. **Directory** 버튼을 클릭하여 클론한 프로젝트 폴더 선택
4. **Finish** 클릭

### 3. 프로젝트 빌드

#### 방법 1: IDE에서 빌드
1. 프로젝트 우클릭 → **Build Project** 선택
2. 또는 단축키: `Ctrl + B`

#### 방법 2: 커맨드라인에서 빌드 (선택사항)
```bash
# Debug 빌드
cd Debug
make clean
make -j4

# Release 빌드 (Release 구성이 있는 경우)
cd Release
make clean
make -j4
```

### 4. 펌웨어 플래싱

1. STM32G474RE 보드를 컴퓨터에 연결 (ST-Link USB)
2. **Run** → **Debug** (F11) 또는 **Run** (Ctrl+F11)
3. 자동으로 플래싱 및 디버깅 시작

## 프로젝트 구조

```
├── Core/
│   ├── Inc/          # 헤더 파일
│   ├── Src/          # 소스 파일
│   └── Startup/      # 스타트업 코드
├── Drivers/
│   ├── CMSIS/        # ARM CMSIS 라이브러리
│   └── STM32G4xx_HAL_Driver/  # STM32 HAL 드라이버
├── Debug/            # 빌드 출력 (gitignore됨)
├── *.ioc             # STM32CubeMX 구성 파일
└── *.ld              # 링커 스크립트
```

## 주의사항

- `.gitignore`에 의해 빌드 출력물(`Debug/`, `Release/`)은 저장소에 포함되지 않습니다
- 처음 클론 후 빌드하면 자동으로 필요한 출력 디렉토리가 생성됩니다
- `.ioc` 파일을 수정한 경우 STM32CubeMX로 코드 재생성이 필요할 수 있습니다

## 문제 해결

### 빌드 오류 발생 시
1. **Project** → **Clean...** 실행
2. 프로젝트 재빌드

### HAL 드라이버 누락 시
- `Drivers/` 폴더가 제대로 클론되었는지 확인
- STM32CubeMX로 `.ioc` 파일 열어서 코드 재생성

### 디버거 연결 실패 시
- ST-Link 드라이버가 설치되어 있는지 확인
- 보드가 제대로 연결되어 있는지 확인
- 다른 디버깅 세션이 실행 중인지 확인
