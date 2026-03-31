# Midgard Pirates Web Portal – MMORPG Companion Platform

## Project Context

This project was developed as the official web portal for a Tales of Pirates private server.

The main goal of the website was to provide a friendly interface for players to manage their accounts, stay informed about server updates, and explore gameplay-related data.

From the administrative side, the portal also provides tools for inspecting player accounts and interacting with game-related information stored in the server databases.

The web application acts as a bridge between the community and the game infrastructure, exposing selected data from the server databases in a structured and accessible way.


---

## Portal Goals

The portal was designed with two main audiences in mind:

**Players**
- Create and manage game accounts
- Access news and server announcements
- Check character rankings and server statistics
- Explore game database information such as mobs and items

**Administrators**
- Inspect player accounts and characters
- Search for specific items or inventory data
- Manage site content such as news and downloads


---

## Core Features

### Account System

The portal includes a full account management system integrated directly with the game server databases.

Players can:

- register new game accounts
- log into the web portal
- view account information
- access a personal dashboard showing their characters

The authentication system connects directly to the same account database used by the game server.


---

### Player Dashboard

After logging in, players can access a dashboard displaying:

- account information
- character list
- server-related account data

This provides a convenient way for players to inspect their in-game progress outside the game client.


📷 Screenshot suggestion  
`screenshot-here: player dashboard overview`


---

### Ranking System

The portal includes a ranking page that retrieves character information from the game database and displays top players.

Ranking information includes:

- character name
- level
- class
- guild association

---

### Game Database Explorer

One of the main features of the portal is a searchable database viewer.

This interface allows players to explore game data such as:

- monsters
- items
- gameplay-related records

The system uses cached JSON datasets generated from game resources to provide fast queries and filtering.

---

### News and Downloads

The site includes a simple content system that allows administrators to publish updates and manage downloadable content.

Features include:

- news publishing
- editing and deleting news entries
- managing game client download links

---

### Server Status

The portal provides real-time server information including:

- server availability
- online player count

This allows players to quickly check if the server is running before launching the game.

---

### Administrative Tools

The admin panel provides additional tools for managing and inspecting game-related data.

Administrative features include:

- searching characters by account
- inspecting inventory or item presence
- managing news and downloads
- reviewing account information

These tools provide operational visibility for server administrators and game masters.


---

## Architecture

The web application is implemented as a full-stack Next.js application.

Key architectural elements include:

- **Next.js App Router** for pages and API routes
- **React + TypeScript** for the frontend
- **TailwindCSS** for styling
- **SQL Server integration** for game data
- **Docker + Nginx** for deployment

The application follows a monolithic structure where frontend pages, API routes, and business logic coexist in a single repository.


### Project Structure
app/
pages and API routes

libs/
database access and business logic

components/
reusable UI components

context/
authentication state

public/
static assets and content files

data/
configuration files


This structure allows clear separation between UI components, backend logic, and configuration data.


---

## Development Challenges

The main challenge during development was translating the game server database structure into a user-friendly web interface.

Game server databases often contain complex and non-intuitive schemas designed primarily for internal server logic rather than human interaction.

As a result, much of the development effort involved:

- understanding the relationships between account and character data
- mapping database structures into readable UI views
- building tools capable of interpreting game-related records in a meaningful way

Once the data model was understood, most of the remaining features were implemented without major difficulties.


---

## Outcome

The final result is a functional web portal that integrates directly with the MMORPG server infrastructure.

It provides:

- a convenient interface for players
- operational tools for administrators
- a centralized information hub for the game community

The project also served as practical experience in full-stack web development, database integration, and building companion platforms for online game servers.


---

## Technologies Used

- **Next.js**
- **React**
- **TypeScript**
- **TailwindCSS**
- **Microsoft SQL Server**
- **Docker**
- **Nginx**
