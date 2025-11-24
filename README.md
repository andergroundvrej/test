
# 🎮 Pong CLI - Terminal-Based Multiplayer Game
A real-time multiplayer Pong game built with TypeScript that runs entirely in your terminal. Connect with opponents, compete in ASCII-rendered matches, and experience classic Pong gameplay through a beautiful command-line interface.

---

## ✨ Features

- 🎯 **Real-time multiplayer** - Play against opponents using WebSocket connections
- 🎨 **ASCII graphics** - Beautiful terminal rendering with color-coded elements
- 🔐 **Authentication system** - User registration and login with 2FA support
- 🎮 **Queue-based matchmaking** - Automatic opponent finding
- 📊 **Live scoring** - Real-time score updates during gameplay

```bash
  make
```
This command will:
- Install all necessary dependencies
- Compile the TypeScript code
- Launch the CLI program

You will also need a .env file that will containt a variable HOST_NAME that will make the requests to the right URL.


### 1. Main Menu

<div align="center">
  <img width="680" height="101" alt="Screenshot from 2025-11-24 17-44-27" src="https://github.com/user-attachments/assets/0fc3b812-08a6-47ad-ab8d-b5f73eae483f" />
</div>

When you first launch the CLI, you'll see an interactive menu. Use the **arrow keys** to navigate between options:

- **Login** - Access an existing account
- **Create Account** - Register a new user
- **Exit** - Close the application

### 2. Queue System

After logging in, you can:

- **Join Queue** - Enter matchmaking to find an opponent
- **Leave Queue** - Exit matchmaking
- **Quit** - Return to the main menu

<div align="center">
  <img width="685" height="124" alt="Screenshot from 2025-11-24 17-44-44" src="https://github.com/user-attachments/assets/c56f5748-155e-431e-b3fe-f505fdc2d784" />
</div>

Once you find an opponent after some seconds, you will have a little window that will tell you to press Space to start the game. So you guessed it, the game will not start until you or your opponent presses Space.

### 4. Controls

<div align="center">

| Key   | Action             |
| ----- | ------------------ |
| W     | Move Paddle Up     |
| S     | Move Paddle Down   |
| Space | Start Game (Ready) |
| Q     | Quit / Forfeit     |

</div>

At the end, after you've played enough and you want to clear some space on your device, you can use this command to delete all the node_modules.

```bash
  make fclean
```

or

```bash
  make clean
```

The CLI connects to a backend API using WebSockets for real-time gameplay. Here's how the flow works:

```mermaid
flowchart TD
A([Start]) --> J[CLI Menu]
J --> Z[Exit]
J --> C{create account}
J --> B{Login}
B -- Failed --> I[error]
I --> J
C -- Failed --> I
B -- Success --> D{Join queue/ Leave queue}
D -- Quit --> E[EXIT]
C -- Success --> J
D -- In queue --> F[finding opponent]
F -- Opponent finded --> G[Game Start]
G -- Q --> H[quit]
G -- W/S --> Y[move paddle]
```

Hope you will enjoy the game and the project!
