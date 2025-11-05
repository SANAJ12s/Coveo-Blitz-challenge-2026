# Coveo-Blitz-challenge-2026
A simple challenge to get accepted into Coveo Blitz Hackaton

# 🌿 Mycelium Connection Network Challenge

> “The mycelium network spans vast distances, connecting all life forms in nature's most sophisticated communication system.”  
> — *Dr. Suzanne Simard*

---

## 🧩 What's This About?

Build biomass networks to connect colonies and score points.  
It’s all about **smart resource allocation and timing** — colony values fluctuate predictably, so plan ahead.

Connect colonies with biomass pathways to earn points.  
The **more valuable the connected colonies** and the **stronger your connection**, the higher your score.

---

## 🗺️ How It Works

### The Map
- Everyone plays on the **same set of maps** with fixed colony positions.
- Colonies have values that **change predictably over time** (you can see future values!).
- You place biomass on map tiles to create connections.

---

## 🧮 Scoring

Scoring is based on the **multiplication of nutrient values** of each pair of connected colonies,  
limited by the strength of their biomass connections.

For each connected colony pair:

connection_strength = weakest_biomass_tile_in_path
points = min(colony1_value, connection_strength) × min(colony2_value, connection_strength)

yaml
Copy code

> 🧠 **Key Insight:** Your connection is only as strong as its weakest link.

---

## 🔋 Resources

- Limited **biomass operations per turn** (add/remove biomass from tiles).  
- You can see **how much biomass** you can move each turn.  
- Plan ahead using **future colony values** to time your investments.

---

## 🤖 Getting Your Bot Ready

Your bot receives a **game state** each turn and must return a list of actions.

### Actions

Two types of actions are available:

#### AddBiomass
Put biomass on a map position.

```json
{
  "type": "ADD_BIOMASS",
  "position": Position,
  "amount": number
}
RemoveBiomass
Remove biomass from a map position.

json
Copy code
{
  "type": "REMOVE_BIOMASS",
  "position": Position,
  "amount": number
}
🧠 Game State
The game state contains everything you need:

Current scores

Colony positions and values

Future colony values

Biomass movement limits

Current biomass map

Example Classes
typescript
Copy code
class Position {
  x: number;
  y: number;
}

class Colony {
  id: string;
  position: Position;
  currentValue: number;
  futureValues: Array<number>;
}

class BiomassAction {
  type: "ADD_BIOMASS" | "REMOVE_BIOMASS";
  position: Position;
  amount: number;
}

class GameState {
  currentTick: number;
  scores: Array<{teamId: string, score: number}>;
  colonies: Array<Colony>;
  biomassMap: Array<Array<number>>; // Current biomass on each tile
  remainingBiomassOperations: number;

  // Map information
  mapWidth: number;
  mapHeight: number;
}
🧭 Grid Indexing Convention
The grid uses the convention:

css
Copy code
biomass[x][y]
Where:

x = column

y = row

Use position.x as the first index and position.y as the second.

🧑‍💻 Available Languages
Choose your language — starterkits are in /starterkits/{language}/.

Python 3.10

Node.js 22

Java 21

.NET 9

🎯 The Goal
Connect colonies with biomass pathways to score points.
The more valuable the connected colonies and the stronger your connection, the more points you get.

📦 Download the Starter Packages
Each starter package includes:

A basic bot (Bot.xyz) as a starting point.

Server communication code (do not edit).

Available Versions
Python 3.10

Node.js 22

Java 21

.NET 9

💻 Run the Challenge Locally
Download and play locally to test your bot.

On Windows
bash
Copy code
cd windows-x64
.\blitz-challenge-win.exe
On macOS/Linux
bash
Copy code
cd [linux-x64|macos-x64]
chmod +x blitz-challenge-[linux|macos]
./blitz-challenge-[linux|macos]
🔗 Download Links
Windows

macOS

Linux

⚙️ Note: On macOS, you must grant permission to run the file.
See this documentation for details.

pgsql
Copy code

Would you like me to add a **table of contents** and **syntax highlighting (JSON/TS blocks styled)** to make it GitHub-friendly?
