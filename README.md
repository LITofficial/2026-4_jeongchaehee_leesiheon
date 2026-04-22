# 세션 정보

## 세션 제목: 인스타, 노션도 AI가 읽고 쓸 수 있을까? MCP 내부 알아보기**

## 세션 자료
- [Microsoft Learn 실습 원본: Azure App Service로 배포하는 FastAPI + PostgreSQL 레스토랑 리뷰 앱](https://learn.microsoft.com/azure/app-service/tutorial-ai-model-context-protocol-server-python?wt.mc_id=studentamb_482865)
- [컨텐츠 설계도](https://www.notion.so/LIT-4-333ab05f4ff28097a42cddc1fd8413ad?source=copy_link)
- [PPT 원본](https://docs.google.com/presentation/d/1hMlO15SjUK3c5397QtLXlnDeGIds2IJY/edit?usp=sharing&ouid=112468629457417043834&rtpof=true&sd=true)

## Azure App Service로 배포하는 FastAPI + PostgreSQL 레스토랑 리뷰 앱
---
page_type: sample
languages:
- azdeveloper
- python
- bicep
- html
- css
- scss
products:
- azure
- azure-app-service
- azure-postgresql
- azure-virtual-network
urlFragment: msdocs-fastapi-postgresql-sample-app
name: Deploy FastAPI application with PostgreSQL on Azure App Service (Python)
description: This project deploys a restaurant review web application using FastAPI with Python and Azure Database for PostgreSQL - Flexible Server. It's set up for easy deployment with the Azure Developer CLI.
---
<!-- YAML front-matter schema: https://review.learn.microsoft.com/en-us/help/contribute/samples/process/onboarding?branch=main#supported-metadata-fields-for-readmemd -->

이 저장소는 FastAPI와 PostgreSQL로 만든 레스토랑 리뷰 웹 애플리케이션입니다.

Azure App Service에 배포할 수 있도록 구성되어 있고, MCP(Model Context Protocol) 도구를 통해 GitHub Copilot Chat 같은 AI 클라이언트가 실제 앱 데이터를 읽고 답할 수 있습니다.

## 이 Repository에서 할 수 있는 것

- 리뷰 작성과 조회가 가능한 레스토랑 웹앱 실행
- Azure Database for PostgreSQL - Flexible Server에 데이터 저장
- Azure App Service로 배포
- MCP 서버 연결로 AI 클라이언트에서 실시간 데이터 조회

## 빠른 시작

가장 쉬운 방법은 GitHub Codespaces에서 여는 것입니다.

1. 이 저장소를 본인 계정으로 Fork합니다. 방법은 [Fork a repo](https://docs.github.com/get-started/quickstart/fork-a-repo)를 참고하세요.

1. Fork한 저장소의 루트에서 **Code** > **Codespaces** > **+**를 선택합니다.

1. Codespaces 터미널에서 아래 명령을 실행합니다.

    ```shell
    cp .env.sample .env
    python -m pip install -r src/requirements.txt
    python -m pip install -e src
    python -m uvicorn fastapi_app:app --reload --port=8000
    ```

1. `Your application running on port 8000 is available.` 메시지가 보이면 **Open in Browser**를 클릭합니다.

## 로컬에서 실행하기

VS Code나 GitHub Codespaces에서 바로 실행할 수 있습니다.

```sh
python -m uvicorn fastapi_app:app --reload --port=8000
```

리포지토리 루트에서 직접 실행할 때는 `src/`로 이동한 뒤 아래처럼 실행하면 됩니다.

```sh
cd src
python -m pip install -r requirements.txt
python -m pip install -e .
python -m uvicorn fastapi_app:app --reload --port=8000
```

브라우저에서는 `http://localhost:8000`을 열면 됩니다.

## 기술 스택

- FastAPI
- PostgreSQL
- Jinja 템플릿
- Azure App Service
- Azure Database for PostgreSQL - Flexible Server
- MCP / FastMCP

## Azure 배포

Azure App Service 기준으로 배포할 수 있도록 구성되어 있습니다.

### 학생이라면 무료 크레딧으로 배포해 볼 수 있습니다

학생 자격이 있다면 [Azure for Students](https://azure.microsoft.com/free/students/)를 통해 신용카드 없이 가입하고, 제공되는 무료 크레딧으로 이 샘플을 배포해 볼 수 있습니다. 정식 배포 전에 연습용으로 써보기 좋습니다.

배포 순서는 다음과 같습니다.

1. [무료 Azure 계정](https://azure.microsoft.com/free/)을 만들고 Azure Subscription을 준비합니다.
2. [Azure Developer CLI](https://learn.microsoft.com/azure/developer/azure-developer-cli/install-azd)를 설치합니다. Codespaces나 VS Code Dev Containers를 쓰면 이 단계는 이미 준비되어 있을 수 있습니다.
3. Azure에 로그인합니다.

    ```shell
    azd auth login
    ```

4. 리소스를 생성하고 배포합니다.

    ```shell
    azd up
    ```

    실행 중에 `azd` 환경 이름, 사용할 구독, 배포 지역을 순서대로 선택하게 됩니다. 배포가 실패하면 지역을 바꿔보는 것도 도움이 될 수 있습니다.

5. 배포가 끝나면 출력된 엔드포인트 주소로 접속해 앱 첫 화면을 확인합니다.

6. 코드만 수정한 뒤 다시 배포할 때는 아래 명령을 사용합니다.

    ```shell
    azd deploy
    ```

## MCP 사용 방식

이 샘플은 앱을 MCP 클라이언트와 연결하는 흐름도 함께 보여줍니다.

- `stdio`는 로컬에서 프로세스를 직접 띄워 연결하는 방식입니다.
- `http`는 배포된 서버 URL로 연결하는 방식입니다.
- MCP 서버를 배포하면, 다른 컴퓨터의 `mcp.json`에 HTTP 주소만 추가해서 같은 도구를 바로 재사용할 수 있습니다.

외부 MCP를 붙일 때는 보통 Smithery 같은 곳에서 서버 URL을 복사한 뒤, VS Code에서 `Cmd+Shift+P`를 눌러 Command Palette를 엽니다. 그다음 MCP 추가 명령을 실행하고 URL을 붙여 넣으면, 원하는 도구를 내 VS Code 환경에 연결할 수 있습니다.

이 방식 덕분에 GitHub Copilot Chat 같은 AI 클라이언트가 파일 업로드 없이 실제 앱 데이터를 읽고 답할 수 있습니다.

## 데모 흐름

1. `mcp.json`에 `restaurant`, `instagram`, `notion` 서버가 등록된 상태를 보여줍니다.
2. 배포된 웹앱에서 리뷰를 직접 작성합니다.
3. GitHub Copilot에게 레스토랑 방문자 이름과 평점을 물어봅니다.
4. Smithery 같은 외부 서비스에서 Instagram, notion MCP URL을 복사한 뒤, VS Code에서 `Cmd+Shift+P` > MCP 추가를 통해 `mcp.json`에 붙여 넣습니다.
5. Copilot이 등록된 도구를 읽고 답변하는 과정을 확인합니다.

## 도움말

이 프로젝트를 사용하다가 문제가 생기면 [Issues](/issues)에 남겨주세요!
