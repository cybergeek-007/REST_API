# REST API

<!-- **Date:** 10 Feb 2026  
**Student:** Ritesh  
**Email:** ritesh1428.be23@chitkarauniversity.edu.in

--- -->

## Overview

This project implements two REST APIs as per the qualifier requirements:
- `POST /bfhl` - Performs mathematical operations and AI queries
- `GET /health` - Health check endpoint

**Tech Stack:** Node.js + Express.js

---
## Links

- **GitHub Repository:** https://github.com/cybergeek-007/qualifier-api
- **Deployed API:** 
- **/health https://qualifier-api-ds5a.onrender.com/health**
- **/bfhl https://qualifier-api-ds5a.onrender.com/bfhl**
## API Endpoints


### 1. POST /bfhl

Performs one of these operations (exactly one key per request):

| Key | Input | Output |
|-----|-------|--------|
| `fibonacci` | Integer | Fibonacci series array |
| `prime` | Integer array | Prime numbers array |
| `lcm` | Integer array | LCM value |
| `hcf` | Integer array | HCF/GCD value |
| `AI` | Question string | Single-word AI response |

**Success Response Format:**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "data": ...
}
```

**Error Response Format:**
```json
{
  "is_success": false,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "error": "..."
}
```

### 2. GET /health

**Response:**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in"
}
```

---

## Example Requests

### Fibonacci
```bash
curl -X POST https://your-api.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"fibonacci": 7}'
```
**Response:** `[0, 1, 1, 2, 3, 5, 8]`

### Prime Filter
```bash
curl -X POST https://your-api.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"prime": [2, 4, 7, 9, 11]}'
```
**Response:** `[2, 7, 11]`

### LCM
```bash
curl -X POST https://your-api.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"lcm": [12, 18, 24]}'
```
**Response:** `72`

### HCF
```bash
curl -X POST https://your-api.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"hcf": [24, 36, 60]}'
```
**Response:** `12`

### AI Query
```bash
curl -X POST https://your-api.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"AI": "What is the capital city of Maharashtra?"}'
```
**Response:** `"Mumbai"`

---

## Local Setup

```bash
# 1. Install dependencies
npm install

# 2. Create .env file
cp .env.example .env

# 3. Add your Groq API key to .env
# Get free key from: https://console.groq.com

# 4. Start server
npm start
```

Server runs at `http://localhost:3000`

---

## Getting Groq API Key (Free)

1. Visit https://console.groq.com
2. Sign up for free account
3. Go to API Keys section
4. Create new API key
5. Copy and add to `.env` file

---

## Deployment on Render

1. Push code to **public** GitHub repository
2. Go to https://render.com
3. Click **New +** → **Web Service**
4. Connect your GitHub repo
5. Configure:
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
6. Add Environment Variable: `GROQ_API_KEY`
7. Click **Create Web Service**
8. Copy the deployed URL

---

## Project Structure

```
├── server.js          # Main API code
├── package.json       # Dependencies
├── .env.example       # Environment template
└── README.md          # This file
```

---

## Validation & Error Handling

- Exactly one key required per request
- Proper HTTP status codes (200, 400, 500)
- Input validation for all operations
- No crashes - graceful error handling
- API key stored securely in environment variables

---


