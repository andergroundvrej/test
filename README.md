
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
  <img width="700" alt="CLI Main Menu" src="https://github.com/user-attachments/assets/88500e9c-f67a-4978-ada5-2181252cb87d" />
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
  <img width="653" height="140" alt="Screenshot from 2025-11-22 18-40-20" src="https://github.com/user-attachments/assets/a69d582c-ff2b-4ad0-8a7c-9b8c2a9d0ac1" />
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
