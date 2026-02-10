# 🧪 R&D Lab: Figure Skating Physics & Visuals
> 언리얼 엔진 5 기반의 피겨 스케이팅 시네마틱을 위한 핵심 기술 검증(PoC) 리포지토리입니다.

## 🎯 프로젝트 개요
본 프로젝트는 **"고난이도 피겨 동작(Spin, Jump)에서의 의상 시뮬레이션 안정성 확보"**와 **"리얼타임 환경 변화 연출"**을 사전에 검증하기 위해 개설되었습니다.
이곳에서 테스트 된 기능(Blueprints, Assets)은 추후 메인 프로젝트인 `Project-Panorama`에 이관될 예정입니다.

## 🛠️ 검증 목표 (R&D Goals)

### 1. 👗 의상 시뮬레이션 (Cloth Physics)
> **Goal:** 2단 프릴 스커트가 스핀 동작 시 뚫리지 않고, 원심력에 의해 자연스럽게 펴지는지 확인.
- [ ] **Chaos Cloth vs Kawaii Physics 비교:**
    - `Chaos Cloth`: `Anim Drive`와 `Backstop` 설정을 통한 볼륨감 유지 테스트.
    - `Kawaii Physics`: Bone 기반 물리 제어를 통한 충돌 안정성 및 퍼포먼스 비교.
- [ ] **스핀 로직 구현 (BP):**
    - 회전 속도(Angular Velocity)에 따라 물리 강성(Stiffness)을 실시간으로 조절하는 블루프린트 제작.
    - `Idle` (Stiff: 1.0) $\leftrightarrow$ `Spin` (Stiff: 0.1) 전환 시 자연스러운 블렌딩 확인.

### 2. ✨ 마법 변신 연출 (Transformation VFX)
> **Goal:** 캐릭터가 점프하는 순간, 자연스럽게 의상과 헤어가 바뀌는 파이프라인 구축.
- [ ] **Dissolve Shader:**
    - `World Position` 기반의 마스킹으로 캐릭터 움직임과 무관하게 바닥부터 차오르는 효과 구현.
    - `Materials`: Masked 모드와 Dither Temporal AA를 활용한 반투명 이슈 해결.
- [ ] **Groom Binding Swap:**
    - 묶은 머리 $\rightarrow$ 긴 머리로 교체 시 물리(Physics)가 튀지 않고 안착되는지 테스트.

### 3. 🌿 환경 상호작용 (Environment Growth)
> **Goal:** 차가운 빙판 위에서 식물이 자라나는 연출 최적화.
- [ ] **Growing Shader (WPO):**
    - `Vertex Color`를 활용한 잔디/꽃의 성장 애니메이션 구현 (World Position Offset).
    - `Timeline` 노드를 활용한 성장 타이밍 제어.

## 📂 폴더 구조 (Directory)
```text
/Content
    /__POC__            # 검증용 메인 폴더
        /Blueprints     # 물리 제어 및 변신 로직 BP
        /Maps           # 테스트 레벨 (Gym)
        /Characters     # R&D용 더미 캐릭터 (Mixamo)
        /Materials      # Dissolve, Ice, Growth 쉐이더
