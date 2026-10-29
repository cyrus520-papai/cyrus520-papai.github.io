{
  "name": "achroma-perfect",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.19.2",
    "socket.io": "^4.7.5"
  }
}const express = require("express");
const http = require("http");
const path = require("path");
const { Server } = require("socket.io");

const app = express();
const server = http.createServer(app);
const io = new Server(server);

const movies = [
  {
    id: "m1",
    title: "Dune",
    year: 2021,
    genre: "Sci-Fi",
    runtime: "2h 35m",
    rating: 8.0,
    image: "https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "m2",
    title: "The Batman",
    year: 2022,
    genre: "Action",
    runtime: "2h 56m",
    rating: 7.8,
    image: "https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "m3",
    title: "Spider-Man: Across the Spider-Verse",
    year: 2023,
    genre: "Animation",
    runtime: "2h 20m",
    rating: 8.7,
    image: "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "m4",
    title: "Oppenheimer",
    year: 2023,
    genre: "Drama",
    runtime: "3h 0m",
    rating: 8.5,
    image: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "m5",
    title: "Everything Everywhere All at Once",
    year: 2022,
    genre: "Sci-Fi",
    runtime: "2h 19m",
    rating: 8.2,
    image: "https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "m6",
    title: "The Dark Knight",
    year: 2008,
    genre: "Action",
    runtime: "2h 32m",
    rating: 9.0,
    image: "https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=900&q=80"
  }
];

const games = [
  {
    id: "g1",
    title: "Fortnite",
    genre: "Battle Royale",
    players: "Up to 100",
    rating: 4.8,
    image: "https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "g2",
    title: "Minecraft",
    genre: "Sandbox",
    players: "Single or Multiplayer",
    rating: 4.9,
    image: "https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "g3",
    title: "Valorant",
    genre: "FPS",
    players: "5v5",
    rating: 4.7,
    image: "https://images.unsplash.com/photo-1542751110-97427bbecf20?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "g4",
    title: "Rocket League",
    genre: "Sports",
    players: "2v2 / 3v3",
    rating: 4.6,
    image: "https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "g5",
    title: "Apex Legends",
    genre: "Battle Royale",
    players: "Squad-based",
    rating: 4.7,
    image: "https://images.unsplash.com/photo-1547637203-8965cbfa64d4?auto=format&fit=crop&w=900&q=80"
  },
  {
    id: "g6",
    title: "League of Legends",
    genre: "MOBA",
    players: "5v5",
    rating: 4.5,
    image: "https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=900&q=80"
  }
];

const rooms = new Map();

app.use(express.static(path.join(__dirname, "public")));

app.get("/api/catalog", (req, res) => {
  res.json({ movies, games });
});

io.on("connection", (socket) => {
  console.log("User connected:", socket.id);

  socket.on("join-room", ({ roomName, username }) => {
    const safeRoom = (roomName || "lounge").trim().replace(/\s+/g, "-").toLowerCase();
    const safeUsername = (username || "Guest").trim();

    if (!safeUsername) {
      socket.emit("join-error", { message: "Username is required." });
      return;
    }

    if (!rooms.has(safeRoom)) {
      rooms.set(safeRoom, {
        users: new Map(),
        messages: []
      });
    }

    const room = rooms.get(safeRoom);

    if (socket.room && socket.room !== safeRoom && rooms.has(socket.room)) {
      const previousRoom = rooms.get(socket.room);
      if (previousRoom) {
        previousRoom.users.delete(socket.id);
        io.to(socket.room).emit("room-update", {
          roomName: socket.room,
          members: [...previousRoom.users.values()]
        });
      }
    }

    socket.leave(socket.room || safeRoom);
    socket.join(safeRoom);
    socket.room = safeRoom;

    room.users.set(socket.id, safeUsername);

    socket.emit("joined-room", {
      roomName: safeRoom,
      username: safeUsername,
      members: [...room.users.values()],
      history: room.messages.slice(-25)
    });

    io.to(safeRoom).emit("room-update", {
      roomName: safeRoom,
      members: [...room.users.values()]
    });
  });

  socket.on("send-message", ({ roomName, username, message }) => {
    const safeRoom = (roomName || "lounge").trim().replace(/\s+/g, "-").toLowerCase();
    const safeUsername = (username || "Guest").trim();
    const text = (message || "").trim();

    if (!safeRoom || !safeUsername || !text) return;

    const payload = {
      username: safeUsername,
      message: text,
      time: new Date().toISOString()
    };

    const room = rooms.get(safeRoom);
    if (room) {
      room.messages.push(payload);
      if (room.messages.length > 100) {
        room.messages = room.messages.slice(-100);
      }
    }

    io.to(safeRoom).emit("new-message", payload);
  });

  socket.on("disconnect", () => {
    if (!socket.room || !rooms.has(socket.room)) return;

    const room = rooms.get(socket.room);
    room.users.delete(socket.id);

    if (room.users.size === 0) {
      rooms.delete(socket.room);
      return;
    }

    io.to(socket.room).emit("room-update", {
      roomName: socket.room,
      members: [...room.users.values()]
    });
  });
});

app.get("*", (req, res) => {
  res.sendFile(path.join(__dirname, "public", "index.html"));
});

const PORT = process.env.PORT || 3000;
server.listen(PORT, () => {
  console.log("App running on http://localhost:" + PORT);
});
