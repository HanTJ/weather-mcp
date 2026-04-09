# Weather-MCP

IP 위치를 기반으로 현재 날씨 정보를 조회하는 Model Context Protocol (MCP) 서버입니다.

## 주요 기능

- **IP 기반 위치 감지**: IP 주소를 사용하여 사용자의 대략적인 위치를 자동으로 감지
- **현재 날씨 데이터**: 기온, 습도, 이슬점, 날씨状況 제공
- **Open-Meteo API**: 무료 Open-Meteo API 사용 (API 키 필요 없음)

## 설치

```bash
# 저장소 클론
git clone https://github.com/HanTJ/weather-mcp.git
cd weather-mcp

# uv를 사용하여 의존성 설치
uv sync

# 또는 직접 설치
uv add fastmcp requests
```

## 사용 방법

### MCP 서버로 실행

```bash
uv run python main.py
```

### Claude/OpenCode에서 사용

MCP 클라이언트에 서버 연결 설정:

```json
{
  "mcpServers": {
    "weather": {
      "command": "uv",
      "args": ["run", "python", "main.py"]
    }
  }
}
```

### 날씨 조회

연결되면 `get_weather` 도구를 사용하세요:

```
get_weather()
```

다음 데이터를 반환합니다:
- 기온 (°C)
- 상대 습도 (%)
- 이슬점 (°C)
- 날씨 상태 코드

## API 상세 정보

- **위치 감지**: ipinfo.io 사용
- **날씨 데이터**: Open-Meteo API (https://open-meteo.com/)
- **표준 시간대**: GMT (일관된 데이터 조회)

## 기술 스택

- Python 3.12+
- [FastMCP](https://github.com/jlowin/fastmcp) - MCP 프레임워크
- [requests](https://docs.python-requests.org/) - HTTP 클라이언트
- [uv](https://github.com/astral-sh/uv) - 패키지 매니저

## 라이선스

MIT
