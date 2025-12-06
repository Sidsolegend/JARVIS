
JARVIS Realtime AI Assistant

A realtime voice-enabled AI assistant built using LiveKit Agents, Google Realtime Model, and custom tools for weather, web search, and email.
The assistant behaves like Jarvis from Iron Man — sarcastic, classy, and concise — and communicates through a LiveKit room with noise cancellation and live audio.

⸻

⚙️ Features

🎙️ Realtime Voice Assistant

The assistant:
	•	Uses Google’s Realtime Model (voice="Charon")
	•	Responds with speech
	•	Follows a custom Jarvis-like persona

📡 LiveKit Agent Integration
	•	Runs inside a LiveKit room
	•	Handles audio input/output
	•	Enhanced noise cancellation via BVC
	•	Auto-starts session with a greeting

🧰 Built-in Tools

The assistant can call three fully functional tools:

Tool	Function
get_weather(city)	Fetches weather via wttr.in
search_web(query)	DuckDuckGo search using LangChain
send_email(to, subject, msg, cc)	Sends emails via Gmail SMTP

Tools are automatically exposed to the LLM using @function_tool() decorators.

⸻

🧠 LLM Configuration

The assistant uses:

google.beta.realtime.RealtimeModel(
    voice="Charon",
    temperature=0.8,
)

The agent’s behavior is controlled by:
	•	AGENT_INSTRUCTION → Defines the Jarvis persona
	•	SESSION_INSTRUCTION → Controls initial behavior when joining a session

⸻

📂 Project Structure

├── main.py                     # LiveKit agent + tools
├── tools.py                    # Weather, web search, email tools
├── prompts.py                  # Jarvis persona instructions
├── .env                        # Google + Gmail credentials
└── README.md


⸻

🔧 Environment Variables

Create a .env file with:

GMAIL_USER=your@gmail.com
GMAIL_APP_PASSWORD=your_app_password
GOOGLE_API_KEY=your_google_realtime_key

Your Gmail must use an App Password (not your real password).

⸻

🚀 Running the Assistant

1.	Install dependencies:

        pip install livekit-agents livekit-plugins-noise google-cloud langchain-community requests python-dotenv

2.	Run the app:

        python main.py

The agent will:
	•	connect to a LiveKit room
	•	greet the user as Jarvis
	•	respond to voice commands in realtime

⸻

🛠️ Tool Descriptions

🌦️ get_weather(city)

Uses wttr.in API to return a 1-line weather summary.

🔍 search_web(query)

Uses DuckDuckGoSearchRun from LangChain.

✉️ send_email(to, subject, message, cc=None)

Sends mail using:
	•	Gmail SMTP
	•	TLS encryption
	•	App Password authentication

Returns success/failure messages logged through logging.

⸻

🤖 Agent Personality

Your agent is built to act like Iron Man’s JARVIS:
	•	Speaks like a classy butler
	•	Slightly sarcastic
	•	Always replies in one sentence
	•	Must address the user as Sid
	•	When taking action, always acknowledges with phrases like:
	•	“Will do, Sir”
	•	“Roger Boss”
	•	“Check!”

Example:

Sid: “Check the weather in Paris.”
Jarvis: “Will do, Sir — the weather in Paris is cloudy at the moment.”

⸻

🏁 Session Behavior

When a session starts, the assistant automatically says:

“Hi my name is JARVIS, your personal assistant, how may I help you?”

⸻

📄 License

MIT License.

⸻

