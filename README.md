[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/ccnn2509-app-seo-ai-badge.png)](https://mseep.ai/app/ccnn2509-app-seo-ai)

# App SEO AI

Application for SEO automation and AI-powered optimization with Google Ads Keyword Planner integration.

## Features

- Keyword research using Google Ads API
- SERP analysis
- Competitor analysis
- SEO recommendations
- MCP (Model Context Protocol) integration for AI assistants

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Google Ads account with API access
- Google Cloud Platform project with Google Ads API enabled

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/ccnn2509/app-seo-ai.git
cd app-seo-ai
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Copy the example environment file:

```bash
cp .env.example .env
```

Edit the `.env` file and fill in your Google Ads API credentials:

```
# Server Configuration
PORT=3000
NODE_ENV=development

# Google Ads API Configuration
GOOGLE_ADS_DEVELOPER_TOKEN=your_developer_token
GOOGLE_ADS_CLIENT_ID=your_client_id
GOOGLE_ADS_CLIENT_SECRET=your_client_secret
GOOGLE_ADS_REFRESH_TOKEN=your_refresh_token
GOOGLE_ADS_LOGIN_CUSTOMER_ID=your_customer_id_without_dashes

# SERP API Configuration (optional)
SERP_API_KEY=your_serp_api_key
```

### 4. Get Google Ads API refresh token

Run the following command to get a refresh token:

```bash
npm run get-token
```

This will open your browser and guide you through the OAuth2 authentication process. The refresh token will be automatically saved to your `.env` file.

### 5. Start the server

For development:

```bash
npm run dev
```

For production:

```bash
npm start
```

The server will start on the port specified in your `.env` file (default: 3000).

## API Documentation

API documentation is available at `/api-docs` when the server is running:

```
http://localhost:3000/api-docs
```

## MCP Integration

This project includes MCP (Model Context Protocol) integration, allowing AI assistants to use the API. The MCP configuration is in the `mcp.json` file.

To use this with Smithery:

1. Go to [Smithery](https://smithery.ai/)
2. Create a new MCP server
3. Select the `app-seo-ai` repository
4. Configure the server settings
5. Deploy the server

## Available MCP Tools

- `research_keywords` - Research keywords related to a given topic or seed keyword
- `analyze_serp` - Analyze a SERP (Search Engine Results Page) for a given query
- `analyze_competitors` - Analyze competitors for a given keyword or domain
- `_health` - Health check endpoint

## Example Usage

### Research Keywords

```javascript
// Example request to research keywords
fetch('http://localhost:3000/api/keywords/ideas?keyword=seo%20tools&language=en')
  .then(response => response.json())
  .then(data => console.log(data));
```

### Analyze SERP

```javascript
// Example request to analyze SERP
fetch('http://localhost:3000/api/serp/analyze?query=best%20seo%20tools&location=United%20States')
  .then(response => response.json())
  .then(data => console.log(data));
```

### Analyze Competitors

```javascript
// Example request to analyze competitors
fetch('http://localhost:3000/api/competitors/analyze?domain=example.com')
  .then(response => response.json())
  .then(data => console.log(data));
```

## License

MIT