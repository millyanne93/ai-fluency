# My Portfolio Chat Widget — How It Works

## What Is a "Backend"?

A backend is the part of a website that does something a plain page can't. A plain HTML page can show text and images, but it can't remember things, process data, or talk to other services. The backend handles those jobs.

For my chat widget, the backend is a Netlify Function — a small piece of code that runs on a server when someone sends a message through the chat.

## What My Feature Does

My portfolio has a chat widget that lets visitors ask questions about my background, projects, and skills. When someone types a question and clicks send:

1. The question is sent to a Netlify Function (my backend).
2. The function takes the question and sends it to Google's Gemini API.
3. Gemini generates a response based on the information I've provided.
4. The response is sent back to the chat widget and displayed to the visitor.

This is useful because it gives visitors an interactive way to learn about me — they can ask specific questions without having to search through my portfolio pages.

## How the Data Flows

Here's the step-by-step path a message takes:

1. **Visitor types a question** in the chat widget on my portfolio.
2. **The browser sends a request** to my Netlify Function at `/api/chat` with the question.
3. **The Netlify Function** receives the request and checks for a valid API key.
4. **The function sends the question** to Google's Gemini API with a system prompt that tells Gemini to only answer questions about me.
5. **Gemini processes the question** and returns a response.
6. **The function receives the response** and sends it back to the browser.
7. **The chat widget displays the response** to the visitor.

This whole flow happens in a few seconds. The visitor asks a question, and the AI answers it.

## Why This Is Secure

The API key for Gemini is stored as a Netlify environment variable — it never reaches the browser. This means visitors can't see or misuse the key.

## Evidence

Here's a screenshot of the chat widget working in action:

<img width="1366" height="728" alt="2026-08-16" src="https://github.com/user-attachments/assets/3adf96c8-7b36-47ba-9e07-a4359a5f3a59" />

