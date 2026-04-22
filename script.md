# 발표자용 Script

이 파일은 발표할 때만 참고하는 메모입니다.

## 전체 흐름

- 먼저 현재 슬라이드 그림을 보여주고, MCP Client / MCP Server / PostgreSQL / User 관계를 짧게 설명한다.
- 그다음 restaurant MCP 데모를 보여준다.
- 이어서 Instagram MCP를 외부 URL로 연결하는 과정을 보여준다.
- 마지막으로 Notion MCP까지 붙여서, GitHub Copilot Chat이 실제 도구를 읽고 답하는 모습을 보여준다.

## 1. 슬라이드 설명 시작 멘트

"지금 보시는 그림은 MCP가 어떻게 동작하는지 한 장으로 정리한 그림입니다."

"왼쪽은 MCP Client입니다. 여기서는 VS Code 안의 GitHub Copilot이라고 생각하시면 됩니다."

"오른쪽은 MCP Server이고, 가운데는 LLM이 있습니다. 사용자는 Copilot에게 질문만 하고, Copilot은 필요한 경우 MCP Server의 도구를 호출합니다."

"아래쪽의 PostgreSQL은 실제 데이터가 저장되는 곳입니다. 즉, Copilot이 그냥 상상해서 답하는 게 아니라, 실제 DB와 연결된 도구를 통해 응답한다는 점이 핵심입니다."

"오늘은 restaurant, Instagram, Notion까지 연결해서, 이 흐름이 실제로 어떻게 보이는지 보여드리겠습니다."

## 2. 발표 시작 전 한 문장으로 핵심 정리

"MCP는 AI가 외부 도구를 표준 방식으로 연결해서, 실제 데이터를 읽고 쓸 수 있게 해주는 연결 규격입니다."

## 3. restaurant MCP 데모 흐름

### 3-1. 먼저 보여줄 것

- 현재 `mcp.json`에 restaurant와 instagram이 들어가 있는 상태를 보여준다.
- restaurant 서버가 배포된 HTTP 방식으로 연결되어 있다는 점을 짚는다.

### 3-2. 멘트

"먼저 restaurant MCP부터 보겠습니다. 이 서버는 웹앱과 PostgreSQL에 연결되어 있고, Copilot이 도구를 통해 실시간 데이터를 읽을 수 있습니다."

"여기서 중요한 건, 파일을 첨부해서 분석하는 방식이 아니라는 점입니다. Copilot이 도구를 직접 호출해서 데이터베이스에 있는 실제 내용을 가져옵니다."

### 3-3. 웹앱에서 리뷰 작성

- 배포된 Web App 화면을 연다.
- 리뷰를 새로 작성한다.
- 이름, 평점, 리뷰 내용이 실제로 저장되는 모습을 보여준다.

멘트:

"이제 웹 화면에서 리뷰를 하나 직접 작성하겠습니다."

"이렇게 저장된 데이터가 나중에 Copilot 질문의 답변 재료가 됩니다."

### 3-4. Copilot 질문

질문 예시:

"restaurant 방문했던 사람들 이름 추려줘. 그리고 방문자 평점도 남겨줘!"

멘트:

"이제 Copilot에게 물어보겠습니다."

"여기서 중요한 건, 방금 웹 화면에서 입력한 이름과 평점이 실제 응답에 포함되는지 확인하는 것입니다."

"정답처럼 외우는 게 아니라, 실제 DB 데이터를 읽어서 답해야 합니다."

### 3-5. 확인 포인트

- 웹에서 입력한 사용자 이름이 답변에 보이는지 확인
- 평점이 함께 정리되는지 확인
- Copilot이 restaurant 도구를 실제로 사용했는지 확인

멘트:

"이름이 맞게 나오면, Copilot이 실제 도구를 읽고 있다는 뜻입니다."

## 4. Instagram MCP 데모 흐름

### 4-1. 먼저 설명할 것

- Instagram MCP는 외부 서비스에서 가져온 URL을 사용한다.
- Smithery 같은 곳에서 MCP 서버 URL을 복사한다.
- VS Code에서 `Cmd+Shift+P`를 눌러 MCP 추가 명령을 실행한다.
- URL을 붙여 넣고 `mcp.json`에 등록한다.

멘트:

"이제는 외부 MCP를 붙여 보겠습니다."

"Smithery 같은 곳에서 이미 만들어진 MCP 서버 URL을 복사할 수 있습니다."

"VS Code에서 `Cmd+Shift+P`를 누르고 MCP 추가 명령을 실행한 다음, URL을 붙여 넣으면 됩니다."

"이 방식이면 내 컴퓨터에 있는 Copilot이 바로 외부 도구를 사용할 수 있습니다."

### 4-2. 보여줄 포인트

- VS Code의 `mcp.json`에 instagram 서버가 추가되는 모습
- 추가 후 Copilot이 해당 도구를 인식하는 모습

멘트:

"이제 instagram MCP가 연결됐는지 확인해보겠습니다."

"추가가 끝나면 Copilot이 도구 목록을 다시 읽고, Instagram 관련 질문에 답할 수 있게 됩니다."

## 5. Notion MCP 데모 흐름

### 5-1. 먼저 설명할 것

- Notion도 같은 방식으로 외부 MCP를 연결한다.
- URL을 복사해서 VS Code MCP 설정에 추가한다.
- Copilot Chat이 Notion 도구를 읽고 답한다.

멘트:

"마지막으로 Notion도 연결해 보겠습니다."

"Instagram과 마찬가지로, Notion MCP도 URL만 있으면 VS Code에 붙일 수 있습니다."

### 5-2. 질문 예시

아래 중 하나를 상황에 맞게 사용한다.

- "Notion에 정리된 이번 발표 핵심 흐름 요약해줘."
- "Notion에 있는 데모 순서를 간단히 정리해줘."
- "Notion 문서에서 오늘 발표의 핵심 포인트만 뽑아줘."

멘트:

"이제 Copilot이 Notion에 연결된 도구를 읽고 답하는지 확인해보겠습니다."

"여기서 포인트는, Copilot이 단순히 기억으로 말하는 게 아니라 Notion의 실제 내용을 읽는다는 점입니다."

### 5-3. 확인 포인트

- Notion에 있는 문서 내용이 답변에 반영되는지 확인
- Copilot이 instagram, notion, restaurant를 각각 구분해서 사용하는지 확인
- MCP가 여러 도구를 한 번에 연결해주는 구조라는 점을 강조

## 6. 연결 방식 정리 멘트

"정리하면, restaurant는 우리가 직접 만든 MCP 서버를 배포해서 연결했고, Instagram과 Notion은 외부 MCP URL을 가져와서 VS Code에 등록한 방식입니다."

"즉, 로컬에서 만든 도구든 외부에서 가져온 도구든, MCP만 맞으면 Copilot에서 같은 방식으로 사용할 수 있습니다."

## 7. 마무리 멘트

"오늘 핵심은 두 가지입니다. 첫째, MCP는 AI와 외부 도구를 연결하는 표준 방식이라는 점입니다. 둘째, 한 번 연결해두면 Copilot이 실제 데이터와 도구를 읽고 답할 수 있다는 점입니다."

"이제 단순한 챗봇이 아니라, 실제 업무 데이터와 연결된 AI를 만들 수 있습니다."

## 8. 발표 중 기억할 키워드

- MCP Client = VS Code / GitHub Copilot
- MCP Server = restaurant / Instagram / Notion
- Tool = 실제 기능 목록
- PostgreSQL = 실제 데이터 저장소
- HTTP MCP = 배포 후 재사용 가능한 형태
- stdio MCP = 로컬 실행 형태

## 9. 짧은 질문 예시 모음

### Restaurant

- "restaurant 방문했던 사람들 이름 추려줘. 그리고 방문자 평점도 남겨줘!"
- "방금 등록한 리뷰 기준으로 방문자별 별점만 정리해줘."

### Instagram

- "Instagram MCP에 있는 도구가 무엇인지 보여줘."
- "Instagram 관련 도구를 사용해서 최근 데이터를 읽어줘."

### Notion

- "Notion에 정리된 발표 흐름을 요약해줘."
- "Notion 문서에서 오늘 데모 순서를 다시 정리해줘."

## 10. 슬라이드 전환 팁

- 첫 슬라이드에서는 MCP Client / Server / DB 관계를 먼저 설명한다.
- restaurant 데모를 먼저 보여주고, 그 다음 외부 MCP(Instagram, Notion)로 확장한다.
- 발표 마지막에는 "한 번 연결하면 다른 도구도 쉽게 붙인다"는 메시지로 끝낸다.
