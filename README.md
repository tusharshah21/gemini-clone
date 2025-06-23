# Gemini Clone

A React-based clone of Google's Gemini conversational AI interface. This project allows users to interact with the Gemini API, send prompts, and receive AI-generated responses in a chat-like UI.

## Features

- Modern React UI with sidebar and main chat area
- Send prompts and receive responses from Gemini API
- Recent prompts and new chat functionality
- Responsive design

## Getting Started

### Prerequisites

- Node.js >= 18
- npm

### Installation

1. Clone the repository:
   ```sh
   git clone <your-repo-url>
   cd gemini-clone
   ```

2. Install dependencies:
   ```sh
   npm install
   ```

3. Set up your Gemini API key in a `.env` file:
   ```
   VITE_GEMINI_API_KEY=your_api_key_here
   ```

### Running the App

Start the development server:
```sh
npm run dev
```
The app will be available at `http://localhost:5173` (or as indicated in your terminal).

## Project Structure

- `src/components/` - React components for the main UI and sidebar
- `src/context/Context.jsx` - React context for managing global state
- `src/config/Gemini.js` - Gemini API configuration and chat logic
- `src/assets/` - Static assets and icons

## About [`src/config/Gemini.js`](src/config/Gemini.js)

This file handles the integration with the Gemini API using the `@google/generative-ai` package. It exports an async function `runChat(prompt)` that:

- Initializes the Gemini API client with your API key and model name.
- Sets up generation configuration (temperature, max tokens, etc.) and safety settings.
- Starts a new chat session and sends the user's prompt.
- Returns the AI-generated response text.

This abstraction allows the rest of the app to simply call `runChat(prompt)` to interact with Gemini, keeping API logic separate from UI code.

## About [`src/context/Context.jsx`](src/context/Context.jsx)

This file provides a React Context for managing the application's global state, including user input, chat history, loading status, and AI responses. It exports a `ContextProvider` component that wraps the app and supplies state and functions such as:

- `onSent(prompt)`: Handles sending prompts to the Gemini API and updating the UI with the response.
- `newChat()`: Resets the chat state for a new conversation.
- State variables for input, previous prompts, loading, results, and more.

This structure keeps state management and API logic centralized and accessible throughout the app.

## License

This project is for educational