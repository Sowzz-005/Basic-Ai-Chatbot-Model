# Basic-Ai-Chatbot-Model
This project is a lightweight AI chat interface built with HTML, CSS, and vanilla JavaScript that connects directly to Google’s Gemini 2.5 Flash model using the generateContent REST API. Users can type a text prompt, optionally attach an image from their device, and receive an AI-generated response displayed in a chat-style layout
# Overview
- Chat interface built with plain HTML, CSS, and vanilla JavaScript.
- Sends user text messages (and optionally an uploaded image) to the Gemini 2.5 Flash model via the generateContent REST API.​
- Displays user messages and AI responses as chat bubbles, with a small image preview when the user attaches an image.

# Features
- Text input field with Enter-to-send behavior.
- Image picker button that lets users select a local image file.
- Selected image is shown as a rounded preview button and also rendered inside the user chat bubble.
- Multimodal requests: the app sends both { text } and inlineData (base64 image) in contents[0].parts to Gemini.​
- Scrolls chat container automatically to the latest message.

# Tech stack
- Frontend: HTML, CSS, JavaScript (no framework).
- AI model: Google Gemini 2.5 Flash via https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash:generateContent
# How it works
- User types a message into the input and optionally selects an image using the image button.
- When the image changes, it is read with FileReader, converted to base64, and stored in user.file with mime_type and data.​
- On send, the code builds a contents array:
- Always includes { text: user.message }.
- If an image is selected, also adds an { inlineData: { mimeType, data } } part.​
- The app sends a POST request with JSON body and API key in the x-goog-api-key header.​
- The response text is read from candidates[0].content.parts[0].text and rendered in an AI chat bubble.

# Setup
1. Create a Gemini API key from Google AI Studio / Gemini console.​
2. Enable Gemini / Generative Language API for your project in Google Cloud console.​
3. In script.js, replace YOUR_VALID_KEY_HERE (or the placeholder key) with your actual API key.
4. Open index.html in a browser (or serve it with a simple static server).

# File structure
- index.html – main page with chat container, prompt area, buttons, and image input.
- style.css – styling for chat layout, user/AI bubbles, prompt area, and rounded image previews.
- script.js – handles user input, image upload, Gemini API calls, and DOM updates.
# Future improvements
- Add chat history so the model can see previous messages.​
- Show error messages in the UI instead of only in the console.
- Add loading indicators for AI responses and better mobile responsiveness.
