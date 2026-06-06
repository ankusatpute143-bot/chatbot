# AI Customer Support Chatbot

A full-stack AI-based customer support chatbot with a modern WhatsApp-style UI, intelligent responses powered by OpenAI, and MongoDB for chat history storage.

## Features

### Core Features
- **Modern Chat UI**: Clean WhatsApp-style interface with smooth animations
- **Real-time Messaging**: Send messages via input box or Enter key
- **Typing Indicator**: Shows "Bot is typing..." animation while processing
- **Timestamps**: All messages display accurate timestamps
- **Error Handling**: Graceful handling of API failures and empty inputs

### Advanced Features
- **FAQ Quick Buttons**: Predefined buttons for common queries (Order Status, Refund, Delivery, Payment, Help)
- **Intent Detection**: Automatic keyword-based intent detection for faster responses
- **Smart Context**: System prompt with intent-based context for OpenAI
- **Chat History**: All conversations stored in MongoDB with timestamps and intent tracking
- **Responsive Design**: Mobile-friendly UI that works on all screen sizes

## Tech Stack

### Backend
- **Node.js** with Express
- **MongoDB** with Mongoose
- **OpenAI API** (GPT-4o-mini)
- **CORS** for cross-origin requests
- **dotenv** for environment variables

### Frontend
- **HTML5** for structure
- **CSS3** for modern styling (WhatsApp-style)
- **Vanilla JavaScript** for chat logic and API interactions

## Project Structure

```
AIChatbot/
├── backend/
│   ├── config/
│   │   └── db.js              # MongoDB connection
│   ├── controllers/
│   │   └── chatController.js  # Chat logic
│   ├── models/
│   │   └── Chat.js            # MongoDB schema
│   ├── routes/
│   │   └── chatRoutes.js      # API routes
│   ├── utils/
│   │   ├── ai.js              # OpenAI integration
│   │   └── agent.js           # Intent detection
│   ├── .env.example           # Environment variables template
│   ├── package.json
│   └── server.js              # Express server
├── frontend/
│   ├── index.html             # Main HTML file
│   ├── styles.css             # WhatsApp-style CSS
│   └── script.js              # Chat logic
└── README.md
```

## Setup Instructions

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (installed and running)
- OpenAI API key

### Backend Setup

1. **Navigate to backend directory**
```bash
cd backend
```

2. **Install dependencies**
```bash
npm install
```

3. **Create .env file**
```bash
cp .env.example .env
```

4. **Configure environment variables**
Edit `.env` file and add your credentials:
```
MONGO_URL=mongodb://localhost:27017/aichatbot
API_KEY=your_openai_api_key_here
PORT=5000
```

5. **Start MongoDB**
Make sure MongoDB is running on your system:
```bash
# On Windows (if installed as service)
# MongoDB should be running automatically

# Or start manually
mongod
```

6. **Start the backend server**
```bash
npm start
# For development with auto-reload
npm run dev
```

Backend will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend directory**
```bash
cd frontend
```

2. **Open index.html in a browser**
You can simply open `index.html` directly in your browser, or use a simple HTTP server:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js http-server
npx http-server -p 8000
```

Frontend will be available at `http://localhost:8000`

## Usage

1. Open the frontend in your browser
2. Type a message in the input box and press Enter or click Send
3. Use FAQ buttons for quick common queries
4. The bot will respond with intelligent, context-aware answers
5. All conversations are stored in MongoDB

## API Endpoints

### POST /chat
Send a message to the chatbot.

**Request:**
```json
{
  "message": "I want to check my order status"
}
```

**Response:**
```json
{
  "reply": "I can help you with your order. Could you please provide your Order ID?",
  "intent": "order"
}
```

## Intent Detection

The chatbot automatically detects the following intents based on keywords:
- **Order**: order, purchase, buy, shipment, tracking
- **Refund**: refund, return, money back, cancel
- **Delivery**: delivery, shipping, deliver, ship, arrive
- **Payment**: payment, pay, credit card, debit, billing
- **Support**: help, support, assist, contact

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| MONGO_URL | MongoDB connection string | Yes |
| API_KEY | OpenAI API key | Yes |
| PORT | Server port (default: 5000) | No |

## Error Handling

The application includes comprehensive error handling:
- Empty input validation
- API failure handling with user-friendly messages
- MongoDB connection error handling
- OpenAI API error handling

## Customization

### Modify System Prompt
Edit `backend/utils/ai.js` to change the bot's personality:
```javascript
const systemPrompt = "You are a professional customer support assistant...";
```

### Add New Intents
Edit `backend/utils/agent.js` to add new intent detection:
```javascript
const intents = {
  newIntent: {
    keywords: ['keyword1', 'keyword2'],
    response: "Your response here",
    intent: 'newIntent'
  }
};
```

### Customize UI
Edit `frontend/styles.css` to change colors, fonts, and layout.

## Troubleshooting

### MongoDB Connection Issues
- Ensure MongoDB is running: `mongod`
- Check your MONGO_URL in .env file
- Verify MongoDB is accessible on the specified port

### OpenAI API Errors
- Verify your API key is correct
- Check your OpenAI API credits/billing
- Ensure you have internet connectivity

### CORS Errors
- Backend runs on port 5000 by default
- Frontend can run on any port
- CORS is configured to allow all origins in development

## License

ISC

## Support

For issues or questions, please check the troubleshooting section or review the code comments.
