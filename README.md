# 🎤 Voice Automation Agent - Hospital Appointment Scheduling

A complete voice-enabled appointment scheduling system built with FastAPI, Gradio, and speech recognition technologies. Run entirely in Google Colab!

## 🌟 Features

- **Voice Input/Output**: Natural language conversation with speech-to-text and text-to-speech
- **Appointment Management**: List, book, and manage appointments through voice commands
- **RESTful API**: Full FastAPI backend with automatic documentation
- **Real-time Processing**: Instant voice recognition and response
- **User-Friendly Interface**: Gradio web interface accessible via public URL

## 🛠️ Technology Stack

- **FastAPI**: High-performance web framework for APIs
- **Gradio**: Interactive web interface for voice interaction
- **Ngrok**: Public URL tunneling for API access
- **Google Speech Recognition**: Speech-to-text conversion
- **gTTS**: Text-to-speech synthesis
- **Pydantic**: Data validation and settings management

## 📋 Prerequisites

### For Google Colab (Recommended)
- Google account
- Ngrok account (free tier) - Get your auth token from [ngrok.com](https://ngrok.com)

### For Local Setup
- Python 3.8+
- pip
- Virtual environment (recommended)

## 🚀 Quick Start - Google Colab

### Step 1: Setup Ngrok
1. Sign up at [ngrok.com](https://dashboard.ngrok.com/signup)
2. Get your auth token from [dashboard](https://dashboard.ngrok.com/get-started/your-authtoken)
3. Keep this token handy

### Step 2: Run in Colab
1. Open the notebook in Google Colab
2. Run Cell 1 to install dependencies (takes 2-3 minutes)
3. Run Cells 2-8 to setup the system
4. In Cell 9, replace `"YOUR_NGROK_TOKEN"` with your actual ngrok token
5. Run Cell 9 to start the system

### Step 3: Use the System
- The Gradio interface will open automatically with a public URL
- Click the microphone icon to record your voice
- Say your command (examples below)
- Listen to the agent's response

## 💬 Voice Commands Examples

### List Appointments
- "Show me my upcoming appointments"
- "List all schedules"
- "What appointments do I have?"

### Book Appointments
- "Book appointment for John Doe tomorrow at 10 AM"
- "Schedule an appointment for Jane Smith on 2024-12-15 at 2 PM"
- "I want to make an appointment for Bob Wilson next Monday at 3 PM"

### Check Availability
- "What time slots are available?"
- "Show me free slots"
- "When can I schedule an appointment?"

## 📚 API Documentation

Once running, access the interactive API docs at: `{your_ngrok_url}/docs`

### Endpoints

#### `GET /schedules`
Returns all scheduled appointments
```json
{
  "schedules": [...],
  "count": 3
}
```

#### `GET /schedules/upcoming`
Returns only upcoming appointments

#### `GET /available-slots?date=YYYY-MM-DD`
Returns available time slots for a specific date

#### `POST /schedule`
Books a new appointment
```json
{
  "patient_name": "John Doe",
  "date": "2024-12-15",
  "time": "10:00 AM",
  "doctor": "Dr. Smith",
  "reason": "General checkup"
}
```

#### `DELETE /schedules/{schedule_id}`
Cancels an appointment

## 🏗️ Project Structure

```
voice-automation-agent/
├── voice_agent_notebook.ipynb    # Main notebook (run this!)
├── README.md                      # This file
├── requirements.txt               # Dependencies
├── SETUP_GUIDE.md                # Detailed setup instructions
└── DEMO_SCRIPT.md                # Recording demonstration guide
```

## 🎬 Recording Your Demo

### Preparation
1. Ensure the system is running
2. Open the Gradio interface
3. Start screen recording (OBS, QuickTime, etc.)

### Demo Script (5 minutes max)

**Part 1: Introduction (30 seconds)**
- Show the Gradio interface
- Explain the system briefly

**Part 2: List Schedules (1 minute)**
- Say: "Show me my upcoming appointments"
- Show the voice recognition
- Play the audio response
- Highlight the listed appointments

**Part 3: Book Appointment (2 minutes)**
- Say: "Book appointment for Sarah Johnson tomorrow at 3 PM"
- Show the booking confirmation
- Verify by listing appointments again

**Part 4: API Demonstration (1.5 minutes)**
- Open the `/docs` endpoint
- Show the Swagger UI
- Execute a GET request to show appointments
- Show the JSON response

**Part 5: Wrap-up (30 seconds)**
- Summarize features
- Show the GitHub repo

## 🔧 Configuration

### Modify Available Time Slots
Edit the `available_slots` list in Cell 3:
```python
available_slots = [
    "9:00 AM", "10:00 AM", "11:00 AM", "12:00 PM",
    "2:00 PM", "3:00 PM", "4:00 PM", "5:00 PM"
]
```

### Change Doctors List
Modify the `doctor` field in appointment creation

### Adjust Speech Recognition
In `speech_to_text` function, modify recognizer settings:
```python
recognizer.energy_threshold = 4000  # Adjust sensitivity
recognizer.dynamic_energy_threshold = True
```

## 🐛 Troubleshooting

### Audio Not Recording
- Grant microphone permissions in your browser
- Check if browser supports Web Audio API
- Try using Chrome or Firefox

### Ngrok Connection Failed
- Verify your auth token is correct
- Check if you're on free tier (limited connections)
- Restart the kernel and try again

### Speech Recognition Errors
- Speak clearly and at a moderate pace
- Reduce background noise
- Ensure good microphone quality
- Check internet connection (uses Google API)

### API Not Responding
- Check if FastAPI server started successfully
- Verify ngrok tunnel is active
- Wait 5 seconds after starting before making requests

## 🎯 Bonus Features Implemented

✅ **Calendar Integration Ready**
- API endpoints support date-based queries
- Can integrate with Google Calendar, Outlook, etc.
- Available slots dynamically calculated

✅ **Advanced Features**
- Natural language processing for intent detection
- Context-aware responses
- Error handling and validation
- Async API for better performance

## 📦 Local Installation (Alternative)

```bash
# Clone the repository
git clone https://github.com/yourusername/voice-automation-agent.git
cd voice-automation-agent

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set ngrok token
export NGROK_TOKEN="your_token_here"

# Run the notebook
jupyter notebook voice_agent_notebook.ipynb
```

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

MIT License - feel free to use this project for learning and development

## 👨‍💻 Author

Created as a demonstration of voice automation and API integration

## 🙏 Acknowledgments

- FastAPI for the amazing web framework
- Gradio for the intuitive UI components
- Google Speech Recognition for STT capabilities
- gTTS for text-to-speech conversion
- Ngrok for tunneling services

## 📞 Support

For issues and questions:
- Open an issue on GitHub
- Check existing issues for solutions
- Review the troubleshooting section

## 🔮 Future Enhancements

- [ ] Multi-language support
- [ ] Integration with actual calendar systems (Google Calendar API)
- [ ] User authentication and authorization
- [ ] SMS/Email notifications for appointments
- [ ] Reminder system
- [ ] Doctor availability management
- [ ] Patient history tracking

## 📊 Testing

Run the optional test cell (Cell 10) to verify API endpoints:
```python
# Test endpoints programmatically
import requests

response = requests.get(f"{api_url}/schedules")
print(response.json())
```

---

**Ready to get started? Open the notebook in Colab and follow the Quick Start guide!** 🚀
