# Weather-MCP

A Model Context Protocol (MCP) server for retrieving current weather information based on your IP location.

## Features

- **IP-based Location Detection**: Automatically detects your approximate location using your IP address
- **Current Weather Data**: Provides temperature, humidity, dew point, and weather conditions
- **Open-Meteo API**: Uses the free Open-Meteo API for weather data (no API key required)

## Installation

```bash
# Clone the repository
git clone https://github.com/HanTJ/weather-mcp.git
cd weather-mcp

# Install dependencies using uv
uv sync

# Or install directly
uv add fastmcp requests
```

## Usage

### Run as MCP Server

```bash
uv run python main.py
```

### Use with Claude/OpenCode

Configure your MCP client to connect to this server:

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

### Get Weather

Once connected, use the `get_weather` tool:

```
get_weather()
```

Returns current weather data including:
- Temperature (°C)
- Relative humidity (%)
- Dew point (°C)
- Weather condition codes

## API Details

- **Location**: Detected via ipinfo.io
- **Weather Data**: Open-Meteo API (https://open-meteo.com/)
- **Timezone**: GMT (for consistent data retrieval)

## Tech Stack

- Python 3.12+
- [FastMCP](https://github.com/jlowin/fastmcp) - MCP framework
- [requests](https://docs.python-requests.org/) - HTTP client
- [uv](https://github.com/astral-sh/uv) - Package manager

## License

MIT
