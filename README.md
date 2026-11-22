# ✈️ Voyanta AI — Multi-Agent Travel Intelligence Platform

**Explore smarter. Plan better. Travel further.**

Voyanta AI is an AI-powered travel planning platform that transforms natural-language travel requests into structured and personalized travel plans. Built using **LangGraph, LangChain, and Groq**, it uses multiple specialized AI agents to research flights, discover hotels, and generate day-by-day travel itineraries.

The platform aims to simplify travel planning by bringing multiple research and planning tasks into one intelligent workflow.

---

## 🌟 Why Voyanta AI?

Planning a trip often requires visiting multiple websites to compare flights, search for hotels, estimate expenses, and organize sightseeing activities.

Voyanta AI simplifies this process through a multi-agent architecture where specialized AI agents collaborate to generate a complete travel plan from a single user request.

### ✨ Key Features

- ✈️ **Flight Research:** Flight-related information using the AviationStack API.
- 🏨 **Hotel Research:** Hotel discovery and accommodation suggestions using Tavily Search.
- 🧠 **Multi-Agent Architecture:** Specialized agents coordinated through LangGraph.
- 🗺️ **Smart Itinerary Planning:** Generates structured day-by-day travel itineraries.
- 💰 **Budget-Aware Planning:** Considers the user's travel budget when generating recommendations.
- 🌐 **FastAPI Backend:** Provides API endpoints for travel requests.
- 💾 **Conversation Persistence:** PostgreSQL integration for storing conversation state.
- ⚡ **LLM-Powered Responses:** Uses Groq-hosted language models to generate travel recommendations.

---

## 🏗️ System Architecture

Voyanta AI follows a multi-agent workflow in which each agent performs a specialized task.

```text
             USER TRAVEL REQUEST
                      |
                      v
              LANGGRAPH WORKFLOW
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
      FLIGHT       HOTEL      ITINERARY
       AGENT       AGENT        AGENT
          |           |           |
          v           v           v
     AviationStack  Tavily     Trip Planning
          |           |           |
          +-----------+-----------+
                      |
                      v
                FINAL RESPONSE
                      |
                      v
             STRUCTURED TRAVEL PLAN
```

### 🤖 Multi-Agent Workflow

| Agent | Responsibility |
|---|---|
| Flight Agent | Researches flight-related information using AviationStack. |
| Hotel Agent | Searches for hotels and accommodation suggestions using Tavily. |
| Itinerary Agent | Creates a day-by-day travel itinerary based on user requirements. |
| Final Response Agent | Combines the collected information into a structured travel plan. |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangGraph | Multi-agent workflow orchestration |
| LangChain | LLM integration and agent development |
| Groq | LLM inference |
| FastAPI | Backend API development |
| PostgreSQL | Database and conversation persistence |
| AviationStack API | Flight information |
| Tavily API | Web search and hotel research |
| Jinja2 | HTML templating |
| HTML, CSS, JavaScript | Frontend development |
| python-dotenv | Environment variable management |

---

## 📁 Project Structure

```text
Voyanta-AI-Multi-Agent-Travel-Intelligence/
│
├── app.py                  # FastAPI application entry point
├── backend.py              # LangGraph multi-agent workflow
├── test.py                 # Workflow testing
├── requirements.txt        # Project dependencies
├── .env                    # Environment variables (not committed)
├── .gitignore              # Git ignored files
│
├── static/                 # Frontend static assets
│   ├── css/
│   ├── js/
│   └── images/
│
├── templates/              # Jinja2 HTML templates
│
└── tools/                  # External API integrations
    ├── flight tools
    └── web search tools


---

## ⚙️ Prerequisites

Before running Voyanta AI locally, make sure you have:

- Python 3.10 or higher
- PostgreSQL installed and running
- A Groq API key
- A Tavily API key
- An AviationStack API key
- Git installed

---

## 🚀 Installation and Setup

### 1. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Navigate to the project directory:

```bash
cd Voyanta-AI-Multi-Agent-Travel-Intelligence
```

### 2. Create a Conda Environment

```bash
conda create -n travel python=3.11 -y
```

Activate the environment:

```bash
conda activate travel
```

Alternatively, you can use Python's built-in virtual environment.

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the root directory:

```env
GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
AVIATIONSTACK_API_KEY=your_aviationstack_api_key

DEFAULT_ORIGIN_IATA=DAC

DATABASE_URL=postgresql://username:password@localhost:5432/travel_db
```

Replace the placeholder values with your own credentials.

**Important:** Never upload your `.env` file or expose API keys publicly.

### 5. Run the Application

Start the FastAPI application:

```bash
python app.py
```

Open your browser:

```text
http://127.0.0.1:8000/
```

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Checks application health |
| POST | `/api/travel` | Submits a travel planning request |

### Example API Request

```bash
curl -X POST http://127.0.0.1:8000/api/travel \
  -H "Content-Type: application/json" \
  -d '{"message":"Plan a 3-day trip to Tokyo with a budget of $1200"}'
```

---

## 🔄 How It Works

1. **User Input:** The user submits a travel request in natural language.
2. **Flight Research:** The Flight Agent gathers flight-related information.
3. **Hotel Research:** The Hotel Agent searches for accommodation options.
4. **Itinerary Generation:** The Itinerary Agent creates a structured travel schedule.
5. **Final Response:** The Final Response Agent combines the results into a complete travel plan.
6. **Persistence:** Conversation state can be stored using PostgreSQL.

---

## 🎯 Example Use Case

**User Request:**

```text
Plan a complete 7-day trip from Bangladesh to India,
including flights, hotels, sightseeing, and a total budget
under ₹2,00,000.
```

**Expected Output:**

- Recommended travel route
- Flight suggestions
- Hotel recommendations
- Day-by-day sightseeing itinerary
- Estimated travel expenses
- Budget breakdown
- Important travel information

---

## 🔐 Environment Variables

| Variable | Description |
|---|---|
| `GROQ_API_KEY` | API key for Groq LLM inference |
| `TAVILY_API_KEY` | API key for Tavily search |
| `AVIATIONSTACK_API_KEY` | API key for flight information |
| `DATABASE_URL` | PostgreSQL connection string |
| `DEFAULT_ORIGIN_IATA` | Default departure airport IATA code |

---

## 🤝 Contributing

Contributions are welcome!

If you want to improve Voyanta AI:

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Commit your changes.
5. Push your branch.
6. Open a Pull Request.

---

## 🔮 Future Enhancements

- Real-time flight price comparison.
- Live hotel availability and price integration.
- Interactive maps and route visualization.
- Multi-currency budget conversion.
- User authentication and travel history.
- PDF export of travel itineraries.
- More specialized travel agents.
- Improved travel recommendations using user preferences.

---

## 🙌 Acknowledgements

Voyanta AI is built using modern open-source technologies and AI tools, including LangGraph, LangChain, Groq, FastAPI, Tavily, and AviationStack.

---

**⭐ If you find Voyanta AI useful, consider giving this repository a star!**

*Voyanta AI — Explore smarter. Plan better. Travel further.*