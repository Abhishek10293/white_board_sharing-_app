# MERN Realtime Board Sharing App

A collaborative real-time whiteboard and video room application built with React, Node.js, Socket.IO, and PeerJS.  
Users can create or join rooms, draw together on a shared whiteboard, chat, and share video/audio streams using peer-to-peer connections.

---

## Features

- Create and join unique rooms via room codes  
- Real-time collaborative whiteboard with multiple drawing tools (pencil, line, rectangle)  
- Presenter role broadcasts live whiteboard images to all participants  
- Real-time chat within rooms  
- Peer-to-peer video/audio connection setup using PeerJS  
- User presence and roles (host, presenter, participants)  
- Responsive UI with React and Bootstrap  

---

## Frontend Overview

Built using **React** and **React Router**, the frontend includes:

### Components

- **CreateRoomForm:** Generates unique room IDs, allows user to enter their name, creates a PeerJS connection as host and presenter, and notifies backend via Socket.IO.  
- **JoinRoomForm:** Allows users to enter their name and an existing room code to join. Establishes PeerJS connection as a participant.  
- **Forms:** Parent component that renders Create and Join forms side by side.  
- **WhiteBoard:** Canvas-based whiteboard powered by [rough.js](https://roughjs.com/) for sketching rectangles, lines, and freehand pencil strokes. The presenter draws and shares updates in real-time as images; participants receive and display these images.

### Technologies

- React hooks (`useState`, `useEffect`, `useLayoutEffect`)  
- PeerJS for WebRTC peer connections  
- Socket.IO client for realtime events  
- Rough.js for sketchy-style drawing on canvas  
- Bootstrap for responsive styling  

---

## Backend Overview

The backend is built with **Node.js**, **Express**, and **Socket.IO** to support real-time functionality:

### Features

- User and room management with in-memory store (add, remove, get users)  
- Handles socket connections and room joins  
- Broadcasts user join/leave messages  
- Receives and broadcasts real-time whiteboard images from presenter to other users  
- Facilitates real-time text chat within rooms  

### Key Endpoints and Socket Events

- `GET /` — basic welcome route  
- Socket events:  
  - `userJoined` — user joins room, server stores and broadcasts user list  
  - `whiteboardData` — presenter sends canvas image, server broadcasts to others  
  - `message` — sends chat messages to room  
  - `disconnect` — removes user and notifies room on disconnect  

### How to Run

```bash
npm install
node server.js

