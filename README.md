# 🌌 Mandelbrot Kaleidoscope — Fractal Shader

> 브라우저 전체 화면에 실시간으로 끊임없이 변화하고 회전하는 **만델브로 집합 기반 만화경(Kaleidoscope) 패턴**을 렌더링하는 몽환적인 미디어 아트 웹 애플리케이션

![status](https://img.shields.io/badge/status-MVP-7c3aed?style=flat-square)
![tech](https://img.shields.io/badge/WebGL-GLSL-ff6b35?style=flat-square)
![license](https://img.shields.io/badge/license-MIT-22c55e?style=flat-square)

---

## 🤖 생성 정보 (How this was made)

이 프로젝트는 **OpenCode** CLI의 **MiniMax-M3** 모델에 아래 프롬프트를 입력하여 1-shot 으로 생성된 결과물입니다.

### 사용된 프롬프트

> WebGL 쉐이더(GLSL)를 직접 작성하여 브라우저 화면 전체에 실시간으로 끊임없이 변화하고 회전하는 만델브로 집합 기반의 만화경(Kaleidoscope) 패턴을 렌더링해줘. 시간이 지남에 따라 사이키델릭한 색상 팔레트가 부드럽게 순환해야 하며, 마우스 위치에 따라 패턴의 대칭축과 줌 레벨이 왜곡되는 몽환적인 미디어 아트 웹 애플리케이션을 만들어줘.
>
> **Implementation Advice:** Use Raw WebGL or a simple wrapper like TWGL. The core logic should reside in the Fragment Shader (GLSL). Pass time (`u_time`) and mouse coordinates (`u_mouse`) as uniforms to the shader for interactivity. 모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.

### 생성 환경

| 항목 | 값 |
|------|-----|
| **AI 도구** | OpenCode CLI |
| **모델** | `MiniMax-M3` |
| **입력 방식** | 위 프롬프트 1-shot |
| **후처리** | 사람이 README 작성 및 구조 정리 |

---

## ✨ Features

- 🎨 **실시간 만델브로 프랙탈 셰이더** — Fragment Shader(GLSL)에서 직접 계산
- 🌀 **만화경 대칭(N-fold Symmetry)** — 폴더블 좌표 변환으로 회전 대칭 패턴
- 🌈 **사이키델릭 색상 순환** — 시간이 흐르며 HSL 팔레트가 부드럽게 변환
- 🖱️ **마우스 인터랙션** — 마우스 위치에 따라 대칭축과 줌 레벨 왜곡
- 🚀 **Zero-Dependency** — 외부 라이브러리 없이 Raw WebGL만 사용
- 📦 **단일 HTML 파일** — `index.html` 하나만 열면 바로 실행

---

## 🚀 사용법 (Usage)

### 로컬 실행
```bash
# 그냥 파일을 브라우저로 열기
open index.html

# 또는 로컬 서버 (권장)
python3 -m http.server 8000
# → http://localhost:8000 접속
```

> 💡 **Tip:** 일부 브라우저는 `file://` 프로토콜에서 ES module이나 WebGL context 생성에 제한을 둘 수 있으니, 로컬 서버 사용을 권장합니다.

### 컨트롤
- **마우스 이동** — 만화경의 대칭축과 줌 레벨이 실시간으로 왜곡됩니다
- **브라우저 창 크기 변경** — 캔버스가 자동으로 전체 화면을 채웁니다

---

## 🧱 기술 스택

| 항목 | 설명 |
|------|------|
| **렌더링** | Raw WebGL 1.0 / 2.0 (라이브러리 의존 없음) |
| **셰이더 언어** | GLSL (Fragment Shader 중심) |
| **언어** | JavaScript (ES6+) |
| **배포** | 정적 호스팅 (단일 HTML) |

### 핵심 셰이더 Uniforms

| Uniform | 타입 | 설명 |
|---------|------|------|
| `u_time` | `float` | 시간(초) — 색상 순환 + 회전 애니메이션 |
| `u_resolution` | `vec2` | 캔버스 해상도 (픽셀) |
| `u_mouse` | `vec2` | 정규화된 마우스 좌표 (0~1) |

---

## 📂 디렉토리 구조

```
mandelbrot-kaleidoscope/
├── README.md       # 본 파일
└── index.html      # 전체 애플리케이션 (셰이더 + JS + CSS 포함)
```

---

## 🎨 비주얼 컨셉

| 요소 | 설명 |
|------|------|
| **배경** | 완전 검정 `#000` — 프랙탈 색상이 가장 잘 살아남 |
| **색상 팔레트** | HSL 기반 사이키델릭 (마젠타 / 시안 / 옐로우 / 라임 / 바이올렛 순환) |
| **대칭** | 6-fold 또는 8-fold 폴더블 만화경 구조 |
| **회전** | 시간 기반 천천히 회전 + 마우스 위치 기반 미세 왜곡 |
| **줌** | 시간에 따라 줌인/줌아웃 호흡, 마우스로 강제 왜곡 |

---

## 📝 라이선스

MIT License — 자유롭게 사용, 수정, 배포 가능합니다.

---

## 🙏 Credits

- **프랙탈 수학** — Benoit Mandelbrot (1924–2010)
- **만화경 좌표 변환** — 전통 폴더블 대칭 기하학
- **AI 생성** — OpenCode + MiniMax-M3