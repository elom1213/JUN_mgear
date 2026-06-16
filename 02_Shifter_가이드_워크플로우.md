---
tags: [mgear, shifter, rigging, workflow]
---

# Shifter 가이드 워크플로우

> [!info] 이 노트의 기원
> 2026-06-16 대화에서 출발 — "부위별/다중 팔 리깅을 하려면 공식 문서의 어떤 페이지를
> 봐야 하나?"라는 질문에 답하기 위해, 가이드 생성→빌드 절차와 봐야 할 문서 섹션을 정리.
> 질문 원문 → [[05_질문_기록]]

> 상위: [[00_MOC_mgear]] · 개념 배경: [[01_mgear와_Shifter_개요]]

가이드를 만들고 → 컴포넌트를 붙이고 → 리그로 빌드하는 전체 흐름과, 공식 문서에서
각 단계를 어디서 봐야 하는지 정리.

## 전체 흐름

```
1. Guide root 생성        (리그의 뿌리. 모든 컴포넌트가 이 아래에 붙음)
2. 컴포넌트 draw / 추가     (arm_2jnt_01, leg_2jnt_01 등 필요한 것만)
3. 가이드 위치 조정         (관절 위치를 캐릭터 메쉬에 맞춰 배치)
4. 컴포넌트 설정           (side, index, IK/FK, channel host 등)
5. Rig Builder 실행        (가이드 → 실제 조인트 + 컨트롤러 리그)
6. 스키닝 / 컨트롤 조정
```

## 문서에서 볼 위치 (Shifter User Documentation)

📄 `shifterUserDocumentation.html` 안의 섹션들:

| 섹션 | 무엇을 보나 |
|------|-------------|
| **Shifter Guide Manager** | 가이드 루트 생성, 컴포넌트를 추가(draw)하는 UI |
| **Guide Operations** | 컴포넌트 복제·미러·재부모(re-parent) 등 가이드 조작 |
| **Guide Settings** | 가이드 전역 설정 |
| **Rig Builder** | 배치된 가이드를 실제 리그로 빌드 |
| Guide Template Manager / Samples | (참고) 전신 템플릿 불러오기 — 부위별 작업엔 굳이 안 써도 됨 |

> 부위별/크리쳐 리깅의 핵심은 **Guide Manager + Guide Operations**.
> 여기서 빈 가이드에 원하는 컴포넌트만 골라 붙이는 방법을 익히면 된다.

## 메뉴 위치 (Maya 안)

- `mGear > Shifter > Guide Manager` — 컴포넌트 추가/관리
- `mGear > Shifter > Build from selection` (또는 Rig Builder) — 빌드
- `mGear > Shifter > Duplicate / Duplicate Sym` — 컴포넌트 복제·대칭 미러
  (다중 팔을 만들 때 한 팔을 만들고 복제하면 편함 → [[04_다중팔_크리쳐_세팅_노트]])

---

## 관련 노트
- [[03_팔다리_IK_컴포넌트_레퍼런스]]
- [[04_다중팔_크리쳐_세팅_노트]]
- [[99_참고링크]]
