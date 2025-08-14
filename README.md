# Real‑Time Chat Server (Node.js + Socket.IO)

A lightweight Socket.IO server for real‑time chat. It supports join/leave notifications, broadcasting messages to other clients, and keeps an in‑memory map of connected users.

> This README covers: quick start, events, client example, environment vars, production tips (Heroku/Plesk), and troubleshooting.
>
> ## ✨ Features
- 🔌 Real‑time bi‑directional communication with Socket.IO
- 👋 Notify when a user joins (`user-joined`) and leaves (`left`)
- 💬 Broadcast messages to all **other** clients (`receive`)
- 👥 Track users by `socket.id` → user name (in memory)
- 🧩 Minimal code, easy to extend with rooms, auth, and persistence
