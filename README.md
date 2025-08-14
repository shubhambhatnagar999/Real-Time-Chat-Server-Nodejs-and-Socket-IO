# Real‑Time Chat Server (Node.js + Socket.IO)

A lightweight Socket.IO server for real‑time chat. It supports join/leave notifications, broadcasting messages to other clients, and keeps an in‑memory map of connected users.

> This README covers: quick start, events, client example, environment vars, production tips (Heroku/Plesk), and troubleshooting.
>
> ## Features
- Real‑time bi‑directional communication with Socket.IO
- Notify when a user joins (`user-joined`) and leaves (`left`)
- Broadcast messages to all **other** clients (`receive`)
- Track users by `socket.id` → user name (in memory)
- Minimal code, easy to extend with rooms, auth, and persistence

### Works great for local testing
Run it with:
```bash
npm install socket.io
node index.js
# server listens on http://localhost:8000 (WebSocket endpoint)

## Event Contract

| Event              | Direction          | Payload                               | Notes                                       |
|--------------------|--------------------|----------------------------------------|---------------------------------------------|
| `connection`       | server internal    | `socket`                               | Fired when a socket connects                |
| `new-user-joined`  | client → server    | `name: string`                         | Client identifies itself                    |
| `user-joined`      | server → clients   | `name: string`                         | Broadcast to **others** when someone joins  |
| `send`             | client → server    | `message: string`                      | User sends a message                        |
| `receive`          | server → clients   | `{ message: string, name: string }`    | Broadcast to **others**                     |
| `disconnect`       | server internal    | –                                      | Triggered when a client disconnects         |
| `left`             | server → clients   | `name: string`                         | Broadcast to **others** when someone leaves |

---

## Suggested Project Structure

```
socketio-chat/
├─ server.js            # HTTP + Socket.IO production server
├─ index.js             # (optional) raw socket-only server for local tests
├─ package.json
├─ README.md
└─ public/              # (optional) static demo client
   └─ index.html
```

## Deployment

### Heroku
1. Add files:
   ```bash
   echo "web: node server.js" > Procfile
   ```
2. Ensure `server.js` uses `process.env.PORT`.
3. Deploy:
   ```bash
   heroku create
   git push heroku main
   heroku open

## Roadmap Ideas
- Chat rooms & private messages
- Message persistence + history pagination
- Typing indicators / read receipts
- Admin/moderation tools
- File/image messages (with storage service)

---

## License
MIT — do whatever you want, but no warranty.

---

## Credits
Built with using Node.js and Socket.IO.
