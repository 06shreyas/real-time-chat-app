# Server - Express + Socket.IO Chat Backend

This is the backend for the realtime chat application.

It is built with Express and Socket.IO, and manages user presence and room messaging.

## Server architecture

- `index.js`
  - Creates an Express app and HTTP server
  - Attaches Socket.IO to the server
  - Uses `cors()` to allow browser connections from the client
  - Loads `router.js` for the root health-check endpoint
  - Registers Socket.IO event handlers for chat behavior
- `router.js`
  - Responds to `GET /` with a JSON health response
- `users.js`
  - Tracks connected users in memory
  - Provides helpers: `addUser`, `removeUser`, `getUser`, `getUsersInRoom`

## Socket.IO events

- `join`
  - Sent from the client when a user enters a room
  - Expects `{ name, room }`
  - Adds the user to the room and broadcasts join messages
  - Sends updated room user data to all clients
- `sendMessage`
  - Sent when the client submits a chat message
  - Broadcasts the message to everyone in the same room
- `disconnect`
  - Fired automatically when a client disconnects
  - Removes the user and notifies the room

## Running the server

```bash
cd server
npm install
npm start
```

The server listens on `process.env.PORT` or `5000` by default.

## Notes

- The server keeps user state in memory, so restarting the server clears all room data.
- `socket.io` version 2.x is used for compatibility with the client version.
- The root HTTP route is available at `http://localhost:5000/`.
