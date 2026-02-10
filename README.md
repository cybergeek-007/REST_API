# Qualifier REST API



## 📋 Overview

A production-ready REST API implementing mathematical operations and AI-powered queries. Built as part of the qualifier assignment with robust error handling and deployed on Render.

**Tech Stack:** Node.js • Express.js • Groq AI

---

## 🔗 Links

- **GitHub Repository:** [https://github.com/cybergeek-007/qualifier-api](https://github.com/cybergeek-007/qualifier-api)
- **Deployed API:**
  - `/health` [https://qualifier-api-ds5a.onrender.com/health](https://qualifier-api-ds5a.onrender.com/health)
  - `/bfhl` [https://qualifier-api-ds5a.onrender.com/bfhl](https://qualifier-api-ds5a.onrender.com/bfhl)

---

## 🚀 API Endpoints

### 1. `POST /bfhl`

Performs mathematical operations or AI queries. **Exactly one operation per request.**

#### Supported Operations

| Operation | Input Type | Output Type | Description |
|-----------|------------|-------------|-------------|
| `fibonacci` | Integer | Array | Generates Fibonacci sequence |
| `prime` | Integer Array | Array | Filters prime numbers |
| `lcm` | Integer Array | Integer | Calculates Least Common Multiple |
| `hcf` | Integer Array | Integer | Calculates Highest Common Factor |
| `AI` | String | String | AI-powered single-word answer |

#### Response Format

**Success (200):**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "data": <result>
}
```

**Error (400/500):**
```json
{
  "is_success": false,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "error": "<error_message>"
}
```

---

### 2. `GET /health`

Health check endpoint to verify API status.

**Response (200):**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in"
}
```

---

## 📝 Example Requests

### Fibonacci Sequence
```bash
curl -X POST https://qualifier-api-ds5a.onrender.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"fibonacci": 7}'
```
**Response:**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "data": [0, 1, 1, 2, 3, 5, 8]
}
```

### Prime Number Filter
```bash
curl -X POST https://qualifier-api-ds5a.onrender.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"prime": [2, 4, 7, 9, 11]}'
```
**Response:**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "data": [2, 7, 11]
}
```

### LCM Calculation
```bash
curl -X POST https://qualifier-api-ds5a.onrender.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"lcm": [12, 18, 24]}'
```
**Response:**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "data": 72
}
```

### HCF/GCD Calculation
```bash
curl -X POST https://qualifier-api-ds5a.onrender.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"hcf": [24, 36, 60]}'
```
**Response:**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "data": 12
}
```

### AI Query
```bash
curl -X POST https://qualifier-api-ds5a.onrender.com/bfhl \
  -H "Content-Type: application/json" \
  -d '{"AI": "What is the capital city of Maharashtra?"}'
```
**Response:**
```json
{
  "is_success": true,
  "official_email": "ritesh1428.be23@chitkarauniversity.edu.in",
  "data": "Mumbai"
}
```

---

## 💻 Local Development

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- Groq API key ([Get free key](https://console.groq.com))

### Setup Instructions

```bash
# 1. Clone the repository
git clone https://github.com/cybergeek-007/qualifier-api.git
cd qualifier-api

# 2. Install dependencies
npm install

# 3. Create environment file
cp .env.example .env

# 4. Add your Groq API key to .env
# GROQ_API_KEY=your_api_key_here

# 5. Start the development server
npm start
```

Server will run at **`http://localhost:3000`**

---

## 🔑 Getting Groq API Key

1. Visit [https://console.groq.com](https://console.groq.com)
2. Sign up for a free account
3. Navigate to **API Keys** section
4. Click **Create API Key**
5. Copy the key and add to your `.env` file

---

## 🌐 Deployment Guide (Render)

### Step-by-Step Deployment

1. **Push to GitHub**
   - Ensure your code is in a **public** repository
   - Commit all changes including `.env.example`

2. **Create Render Service**
   - Go to [https://render.com](https://render.com)
   - Click **New +** → **Web Service**
   - Connect your GitHub repository

3. **Configure Build Settings**
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
   - **Environment:** Node

4. **Add Environment Variables**
   - Key: `GROQ_API_KEY`
   - Value: Your Groq API key

5. **Deploy**
   - Click **Create Web Service**
   - Wait for deployment to complete
   - Copy your deployed URL

---

## 📁 Project Structure

```
qualifier-api/
├── server.js          # Main Express application
├── package.json       # Project dependencies
├── .env.example       # Environment variable template
├── .gitignore         # Git ignore rules
└── README.md          # Project documentation
```

---

## ✅ Features & Validation

- ✓ **Single Operation Per Request** - Validates exactly one key present
- ✓ **Input Validation** - Type checking and range validation
- ✓ **Error Handling** - Graceful error responses with proper HTTP codes
- ✓ **Security** - API keys stored in environment variables
- ✓ **Production Ready** - Deployed and tested on Render
- ✓ **AI Integration** - Powered by Groq's LLaMA models

---

## 🛠️ Error Handling

The API implements comprehensive error handling:

- **400 Bad Request** - Invalid input or missing required fields
- **500 Internal Server Error** - Server-side errors with detailed messages
- **Graceful Degradation** - No crashes, all errors return JSON responses

---

## 📄 License

This project is created for educational purposes as part of the qualifier assignment.

---

**Made with ❤️ by Ritesh**
