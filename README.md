# Documents

## 요구사항
https://cli.github.com/manual/
깃허브 CLI를 설치하면 편합니다.

또한, 이 페이지는 기본적인 내용만 포함하고 있으므로, 상세한 내용은 공식 문서나 여러가지 찾아주시면 감사하겠습니다.

## 1. 리포지토리에서 따로 브랜치를 생성하는 방법

### 웹페이지에서 생성하기
1. 리포지토리로 이동합니다.
2. 상단에서 브랜치 드롭다운 메뉴를 클릭합니다.
3. 텍스트 필드에 새로운 브랜치 이름을 입력하고, "Create branch" 버튼을 클릭하여 브랜치를 생성합니다.

### 터미널에서 생성하기
1. 로컬 리포지토리로 이동합니다.
2. 다음 명령어를 입력하여 새로운 브랜치를 생성합니다:
```
git checkout -b new-branch-name
```
3. 생성한 브랜치를 원격 리포지토리에 푸시합니다 :
```
git push -u origin new-branch-name\
```

## 2. 따로 생성한 브랜치에서 Main 브랜치에 Pull Request를 하는 방법

### 웹페이지에서 PR 생성하기
1. 변경사항을 커밋한 후, GitHub 리포지토리 페이지로 이동합니다.
2. "Pull requests" 탭을 클릭합니다.
3. "New pull request" 버튼을 클릭합니다.
4. 비교할 브랜치들을 선택합니다. (기본적으로 생성한 브랜치와 Main 브랜치)
5. 변경 내용을 검토하고, "Create pull request" 버튼을 클릭합니다.
6. 필요한 경우, 추가 정보를 입력하고 다시 "Create pull request" 버튼을 클릭하여 PR을 생성합니다.

### 터미널에서 PR 생성하기
1. 변경사항을 커밋하고 원격 브랜치에 푸시합니다:
```
git push origin new-branch-name
```
2. GitHub CLI를 사용하여 PR을 생성합니다:
```
gh pr create --base main --head new-branch-name --title "PR 제목" --body "PR 설명"
```

## 3. 해당 PR을 보고 승낙하여 Merge하는 방법

### 웹페이지에서 Merge하기
1. "Pull requests" 탭으로 이동하여 해당 PR을 클릭합니다.
2. PR의 내용을 확인하고, 필요한 경우 리뷰를 요청하거나 의견을 추가할 수 있습니다.
3. 준비가 되면, "Merge pull request" 버튼을 클릭합니다.
4. "Confirm merge" 버튼을 클릭하여 변경사항을 메인 브랜치에 병합합니다.

### 터미널에서 Merge하기
1. PR을 로컬로 가져옵니다
```
git fetch origin pull/PR번호/head:PR번호
git checkout PR번호
```
2. 변경사항을 로컬 main 브랜치에 병합합니다
```
git checkout main
git merge PR번호
```
3. 병합된 내용을 원격 리포지토리에 푸시합니다
```
git push origin main
```

## 4. 프로젝트 일정 관리 방법

### GitHub Projects 사용하기
1. 리포지토리 또는 조직의 "Projects" 탭으로 이동합니다.
2. 새로운 프로젝트를 생성하거나 기존 프로젝트를 선택합니다.
3. 각 작업에 대한 카드를 생성합니다. 카드는 할 일, 진행 중, 완료와 같은 열에 배치할 수 있습니다.
4. 카드에 기한, 담당자, 레이블 등을 추가하여 작업의 세부 정보를 설정합니다.
5. 작업의 진행 상황에 따라 카드를 이동시켜 일정 관리와 작업 추적을 할 수 있습니다.

### 터미널에서 프로젝트 관리하기

1. GitHub CLI를 사용하여 프로젝트에 대한 작업을 관리할 수 있습니다. 프로젝트 목록을 보려면 다음 명령어를 사용합니다:
```
gh project list
```
2. 특정 프로젝트를 선택하여 상세 정보를 확인할 수 있습니다
```
gh project view 프로젝트번호
```
3. 새로운 작업을 추가하거나 기존 작업을 수정할 수 있습니다
```
gh project card create --project 프로젝트번호 --title "작업 제목" --note "작업 설명"
```
```
gh project card update 카드번호 --title "새로운 제목" --note "새로운 설명"
```

## 5. 프로젝트 및 리포지토리 Issue 관리 방법

### 웹페이지에서 Issue 관리하기
1. 리포지토리 페이지에서 "Issues" 탭을 클릭합니다.
2. "New issue" 버튼을 클릭하여 새로운 이슈를 생성합니다.
3. 이슈의 제목과 내용을 입력하고, 필요에 따라 레이블, 프로젝트, 마일스톤 등을 추가합니다.
4. 이슈가 생성되면 담당자에게 할당하거나, 댓글을 통해 토론을 진행할 수 있습니다.
5. 이슈가 해결되면 "Close issue" 버튼을 클릭하여 이슈를 닫습니다.

### 터미널에서 Issue 관리하기
1. GitHub CLI를 사용하여 이슈를 생성할 수 있습니다
```
gh issue create --title "이슈 제목" --body "이슈 내용"
```

2. 특정 이슈를 조회하거나 업데이트할 수 있습니다
```
gh issue view 이슈번호
```
```
gh issue edit 이슈번호 --title "새로운 제목" --body "새로운 내용"
```
3. 이슈를 완료하면 닫을 수 있습니다
```
gh issue close 이슈번호
```
