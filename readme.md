# ASI1 Deploy Example

A ready-to-deploy AI chat agent built with the **Fetch.ai uAgents** framework and powered by the **ASI1 LLM**. The agent registers on Agentverse, listens for chat messages via the uAgents chat protocol, and responds with AI-generated answers through the ASI1 API.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Fetch.ai](https://img.shields.io/badge/Fetch.ai-1B1464?style=for-the-badge&logo=data:image/svg+xml;base64,&logoColor=white)
![OpenAI SDK](https://img.shields.io/badge/OpenAI_SDK-412991?style=for-the-badge&logo=openai&logoColor=white)
![uAgents](https://img.shields.io/badge/uAgents-3D8BD3?style=for-the-badge)
![tag:asi1-llm-agent](https://img.shields.io/badge/asi1--llm--agent-3D8BD3?style=for-the-badge)
![tag:innovationlab](https://img.shields.io/badge/innovationlab-3D8BD3?style=for-the-badge)

## Features

- **ASI1-Powered Responses** — Sends user queries to the ASI1 LLM (`api.asi1.ai`) via an OpenAI-compatible client and returns intelligent answers
- **uAgents Chat Protocol** — Implements the standard `ChatMessage` / `ChatAcknowledgement` protocol for seamless inter-agent communication
- **Agentverse Registration** — Auto-registers on Fetch.ai Agentverse at startup with a published manifest and README
- **Session Management** — Handles multi-turn conversations with proper message acknowledgement and end-session signalling
- **Concurrent Message Handling** — Processes multiple incoming messages in parallel
- **Mailbox Support** — Uses the uAgents mailbox for reliable message delivery

## Tech Stack

| Component    | Technology                                                        |
| ------------ | ----------------------------------------------------------------- |
| Agent Framework | [uAgents 0.23.6](https://github.com/fetchai/uAgents)          |
| LLM API      | [ASI1](https://asi1.ai/) via OpenAI-compatible SDK                |
| Language     | Python 3.10+                                                      |
| Config       | `python-dotenv` for environment variable management               |

## Getting Started

### Prerequisites

- Python 3.10 or higher
- An [ASI1 API key](https://asi1.ai/)
- An [Agentverse API key](https://agentverse.ai/) (optional, for registration)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/gautammanak1/asi1-deploy-example.git
   cd asi1-deploy-example
   ```

2. **Create a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**

   Create a `.env` file in the project root:

   ```env
   ASI_API_KEY=your_asi1_api_key
   AGENT_SEED_PHRASE=your_unique_seed_phrase
   ILABS_AGENTVERSE_API_KEY=your_agentverse_api_key
   ```

### Run the Agent

```bash
python app.py
```

The agent starts on port **8001** and registers with Agentverse (if credentials are provided).

## Usage

Once running, the agent listens for `ChatMessage` payloads via the uAgents chat protocol:

1. **Send a message** to the agent's address through Agentverse or another uAgent.
2. The agent **acknowledges** the message immediately.
3. It forwards the text to the **ASI1 LLM** and returns the AI-generated response.
4. The session ends after each response with an `EndSessionContent` signal.

## Project Structure

```
asi1-deploy-example/
├── app.py              # Agent definition, chat protocol handlers, Agentverse registration
├── requirements.txt    # Python dependencies
└── README.md
```

## License

This project is open source and available for personal and educational use.
