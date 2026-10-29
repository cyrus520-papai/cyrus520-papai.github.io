{
  "name": "real-social-stream-hub",
  "private": true,
  "scripts": {
    "dev": "concurrently \"npm run server\" \"npm run client\"",
    "server": "node server.js",
    "client": "next dev"
  },
  "dependencies": {
    "express": "^4.19.2",
    "socket.io": "^4.7.5",
    "socket.io-client": "^4.7.5",
    "next": "^14.2.15",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "cors": "^2.8.5"
  },
  "devDependencies": {
    "concurrently": "^9.0.1"
  }
}
