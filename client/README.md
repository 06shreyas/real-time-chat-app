# Client - React Realtime Chat

This is the frontend application for the realtime chat project.

It is built with React 18 and Create React App, and uses Socket.IO client to connect to the backend.

## Client architecture

### Routes
- `/` — **Join screen**
- `/chat` — **Chat screen**

### Main components

- `src/App.js`
  - Defines routes using React Router v5
- `src/components/Join/Join.js`
  - Captures `name` and `room`
  - Sends the user to `/chat?name=...&room=...`
- `src/components/Chat/Chat.js`
  - Connects to the Socket.IO backend
  - Emits `join` when the user enters the room
  - Listens for `message` and `roomData`
  - Renders messages, room info, and active users
- `src/components/Messages/` and `src/components/Messages/Message/Message.js`
  - Displays chat messages with sender and emoji support
- `src/components/Input/Input.js`
  - Allows the user to type and send messages
- `src/components/InfoBar/InfoBar.js`
  - Shows current room name and leave button
- `src/components/TextContainer/TextContainer.js`
  - Displays the list of active users in the room

### Client behavior

- When the user clicks **Sign In** on the Join screen, the app navigates to `/chat` with query parameters.
- `Chat.js` reads `name` and `room` from the URL query.
- The app connects to `http://localhost:5000` using Socket.IO.
- The backend handles room join logic and broadcasts messages to all users in the same room.
- Messages from the current user render in a blue bubble, while others render in a lighter style.

## Running the client

```bash
cd client
npm install
npm start
```

The app will open in the browser, typically at `http://localhost:3000`.

## Build for production

```bash
cd client
npm run build
```

## Notes

- The current client connects to the backend at `http://localhost:5000`.
- If you deploy the backend to a different host, update `src/components/Chat/Chat.js`.
- The app uses `react-scroll-to-bottom` to automatically keep the latest chat message visible.

## Dependencies

- `react@18.2.0`
- `react-dom@18.2.0`
- `react-router-dom@5.3.4`
- `socket.io-client@2.2.0`
- `react-scripts@5.0.1`
- `react-emoji@0.5.0`
- `query-string@6.8.2`

## Development notes

- The project uses the React 18 root API in `src/index.js`.
- The app manages chat state using React hooks: `useState` and `useEffect`.
- User and room state are stored in the URL query string, so refreshing `/chat` preserves the current session if the same query is present.
