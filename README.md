# Realtime Chat Application

A full-stack realtime chat application built with:
- **React** on the client
- **Express** + **Socket.IO** on the server
- **Socket.IO client** for realtime websocket messaging

This repository contains two separate projects:
- `client/` — React frontend
- `server/` — Express + Socket.IO backend

---

## Repository structure

- `client/`
  - React app created with Create React App
  - `src/App.js` configures routing between Join and Chat pages
  - `src/components/Join/Join.js` collects username and room name
  - `src/components/Chat/Chat.js` manages socket connection, join flow, and message state
  - `src/components/Messages/` renders chat messages with auto-scroll
  - `src/components/Input/Input.js` captures chat input
  - `src/components/InfoBar/InfoBar.js` displays room info and leave button
  - `src/components/TextContainer/TextContainer.js` shows active users list

- `server/`
  - `index.js` starts the HTTP + Socket.IO server
  - `router.js` provides a simple health-check route
  - `users.js` manages room membership and user lookups

---

## Features

- Create or join a chat room by name
- Send and receive realtime chat messages in the same room
- See live room user presence updates
- Support multiple chat rooms simultaneously
- Persistent frontend routing for a clean Join/Chat flow

---

## Running the project locally

### 1. Start the server

```bash
cd server
npm install
npm start
```

The backend will listen on `http://localhost:5000` by default.

### 2. Start the client

```bash
cd client
npm install
npm start
```

The frontend will open at `http://localhost:3000` (or the next available port).

### 3. Use the app

- Open the Join page
- Enter a `Name` and `Room`
- Click **Sign In**
- Send realtime chat messages
- Open the same room in another browser tab to test multi-user chat

---

## Notes

- The frontend is currently configured to connect to `http://localhost:5000`.
- The server uses Socket.IO v2 and the client uses `socket.io-client` v2 for compatibility.
- This repo was originally built as a tutorial chat application, so it is ideal for learning realtime websockets and room-based chat flow.

---

## More documentation

- See `client/README.md` for client-specific setup and component details
- See `server/README.md` for server architecture and Socket.IO event documentation

