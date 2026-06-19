# Daily TODO

심플한 데일리 투두 프로그램입니다.

매일 일정한 시간에 프로그램이 실행되도록 설정할 수 있습니다. (아래 설명 참고))

---

## 실행 방법

### 방법 1 — 파일 직접 열기

`todo.html`을 다운로드 받은 후, 브라우저로 열면 바로 실행됩니다.

> 이미지를 사용하려면 `todo.html`과 `images/` 폴더가 같은 위치에 있어야 합니다.

### 방법 2 — GitHub Pages

```python
# https://ahyun39.github.io/Daily_TODO/todo.html
https://[username].github.io/Daily_TODO/todo.html
```

---

## 기능

- **캘린더** — 날짜 클릭으로 해당 날의 할 일 확인. 연도·월 클릭으로 빠른 이동
- **할 일 추가** — 입력 후 Enter 또는 추가 버튼
- **완료 체크** — 체크박스 클릭 시 취소선. 진행률 실시간 표시
- **루틴 관리** — 매일 반복할 항목을 등록하면 해당 날짜를 처음 열 때 자동 추가
- **진행률 이미지** — 완료율에 따라 캘린더에 이미지 표시 (30% 이하 / 70% 이하 / 70% 초과)

---

## macOS 매일 오전 9시 자동 실행

1. todo.html을 원하는 위치에 저장 (예: /Users/[user_name]/[folder_name]/todo.html)

2. `com.user.todo.plist.template` 파일을 다운로드 한 후, `com.user.todo.plist`로 이름 변경

3. plist 안의 경로를 1번에서 저장한 실제 경로로 수정

```xml
<string>/Users/[user_name]/[folder_name]/todo.html</string>
```

4. plist를 macOS LaunchAgents에 등록

```bash
cp com.user.todo.plist ~/Library/LaunchAgents/
launchctl load ~/Library/LaunchAgents/com.user.todo.plist
```

등록 해제:

```bash
launchctl unload ~/Library/LaunchAgents/com.user.todo.plist
```

---

## 데이터 초기화(방법 2로 실행하는 경우)

1. 앱이 열린 브라우저 탭에서 아래 단축키로 개발자 도구를 엽니다
   - **Chrome / Firefox**: `F12` 또는 `Ctrl+Shift+J` (Windows) / `Cmd+Option+J` (Mac)
   - **Safari**: `Cmd+Option+C`
2. **Console** 탭을 클릭합니다
3. 아래 코드를 붙여넣고 Enter를 누릅니다

```js
['paper-todo:todos', 'paper-todo:routines', 'paper-todo:migrated'].forEach(k => localStorage.removeItem(k));
location.reload();
```

4. 페이지가 새로고침되며 모든 데이터가 초기화됩니다


