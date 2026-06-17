# Push 계획서 — JUN_mgear 노트 GitHub 최초 푸시

- **작성일**: 2026-06-16
- **대상 폴더**: `C:\Users\USER\Desktop\JP\0030_maya_python_JUN\JUN_mgear` (Maya_Python repo **밖**의 형제 폴더)
- **Push 대상**: `https://github.com/elom1213/JUN_mgear.git` (현재 **빈** 저장소)
- **기본 브랜치**: `main`
- **인증**: HTTPS + PAT(Personal Access Token) / 자격증명
- **현재 상태**: `JUN_mgear`는 **아직 git 저장소 아님** → `git init` 필요

> ℹ️ 이 계획서는 원래 Maya_Python repo의 `JUN_All/docs/plans/`에 있었으나, 대상이 별도 repo인
> **JUN_mgear vault** 이므로 이 vault의 `_meta/`로 이동했다. 최초 push 는 완료된 상태이며 이 문서는 기록용이다.

---

## 1. 배경 / 목적

[[00_MOC_mgear]] 등 mgear 공부 노트(.md 7개)를 Obsidian vault로 관리 중인데, 이를
GitHub `elom1213/JUN_mgear` 저장소와 동기화하려 한다. 저장소가 비어 있으므로 **최초 push**.

푸시 대상 파일 (현재 `JUN_mgear/`):
```
00_MOC_mgear.md
01_mgear와_Shifter_개요.md
02_Shifter_가이드_워크플로우.md
03_팔다리_IK_컴포넌트_레퍼런스.md
04_다중팔_크리쳐_세팅_노트.md
05_질문_기록.md
99_참고링크.md
```

---

## 2. ⚠️ 사전 확인 사항 (push 전 반드시 점검)

1. **계정 불일치 / 인증**
   - 전역 git 사용자: `Dnable_JunnyPark <junny.park1213@gmail.com>`
   - 대상 repo 소유자: **`elom1213`** (다른 계정), `gh`는 **미로그인** 상태.
   - 최초 HTTPS push 시 **elom1213 계정의 자격증명(PAT)** 을 요구한다.
     Windows 자격증명 관리자(Credential Manager)에 다른 계정이 캐시돼 있으면 충돌 가능
     → 필요 시 해당 항목 갱신 또는 PAT 입력.
   - **커밋 작성자(author)**: 기본값은 `Dnable_JunnyPark`로 찍힌다. elom1213 명의로
     남기고 싶으면 이 repo에 **로컬 user 설정**을 따로 적용(아래 3-b, 선택).

2. **빈 저장소 여부 확인**: 원격에 README/라이선스 등 초기 커밋이 있으면 push가 거부될 수
   있다(non-fast-forward). 그 경우 `git pull --rebase` 후 push 또는 강제 정렬 필요.
   현재는 "비어 있음"으로 전제.

3. **줄바꿈(CRLF)**: Windows라 `core.autocrlf` 경고가 날 수 있음. 노트(.md)뿐이라 무해.

---

## 3. 실행 단계

> 모든 명령은 **`JUN_mgear` 폴더 안에서** 실행. (Maya_Python이 아님)

### a) 저장소 초기화 + .gitignore + (선택)README

`.gitignore` 생성 — Obsidian 설정/캐시 제외:
```gitignore
# Obsidian
.obsidian/
.trash/

# OS
Thumbs.db
.DS_Store
```

(선택) `README.md` 한 줄: `# JUN_mgear — mgear 공부 노트 (Obsidian vault)`

### b) (선택) 이 repo만 커밋 작성자를 elom1213로

```bash
git init -b main
git config user.name  "elom1213"
git config user.email "<elom1213 계정 이메일>"
```
> elom1213 명의가 필요 없으면 이 두 줄은 생략(전역 Dnable_JunnyPark로 커밋됨).

### c) 최초 커밋 + 원격 연결 + push

```bash
# JUN_mgear 폴더에서
git init -b main                         # 이미 b)에서 했다면 생략
git add .gitignore README.md *.md        # 노트 + 설정 파일
git status                               # .obsidian 빠졌는지 확인
git commit -m "docs(mgear): initial mgear study notes (Obsidian vault)"

git remote add origin https://github.com/elom1213/JUN_mgear.git
git push -u origin main                  # 최초 push (인증 프롬프트 → elom1213 PAT)
```

---

## 4. 검증 (push 후 확인)

- [ ] `git remote -v` → origin = `https://github.com/elom1213/JUN_mgear.git`
- [ ] `git log --oneline` → 최초 커밋 1개, author 의도대로(Dnable 또는 elom1213)
- [ ] GitHub 웹에서 `elom1213/JUN_mgear` 에 .md 7개 + README + .gitignore 표시
- [ ] `.obsidian/` 폴더가 **푸시되지 않았는지** 확인(아직 Obsidian으로 vault를 안 열었으면
      애초에 없을 수도 있음)
- [ ] 한글 파일명이 GitHub에서 깨지지 않고 보이는지 확인

---

## 5. 향후 동기화 (참고)

- 노트 수정 후: `git add -A && git commit -m "docs(mgear): ..." && git push`
- 이 repo의 push 대상은 **`origin` (elom1213/JUN_mgear)** — Maya_Python의 기본
  `Dnable_repo/dev` 와는 **무관**. 두 repo를 헷갈리지 말 것.
