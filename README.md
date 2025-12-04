# Tonica

**Tonica** is a sleek and intuitive mobile music player built with **React Native**, **Expo**, and **TypeScript**. It is designed for smooth user experience and includes essential features such as music playback, playlists, and a modern interface.

---

## Table of Contents

- [Features](#features)  
- [Tech Stack](#tech-stack)  
- [Architecture](#architecture)  
- [Folder Structure](#folder-structure)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Future Improvements](#future-improvements)

---

## Features

- Play, pause, skip, shuffle, and repeat tracks  
- Browse and search local music library  
- Create and manage playlists  
- Now Playing screen with album art and song metadata  
- Background playback with lock screen controls  
- Light & Dark mode support  

---

## Tech Stack

- **React Native & Expo** – cross-platform mobile development  
- **TypeScript** – type safety and maintainability  
- **expo-av** – audio playback  
- **Expo Router** – filesystem-based routing for screens  
- **React Context + Hooks** – global state management  

---

## Architecture

Tonica follows a **modular architecture**, separating UI, business logic, state management, and services for scalability and maintainability.

### **1. App Router**
- Uses **filesystem-based routing** (`app/` directory) with Expo Router.  
- `_layout.tsx` defines shared layout, including **tabs** (Home, Library, Playlists).  
- Each `.tsx` file in `app/` represents a route (`index.tsx` → Home, `library.tsx` → Library, etc.).  

### **2. Screens**
- **UI-focused** components representing app pages.  
- Examples: `HomeScreen`, `LibraryScreen`, `PlaylistsScreen`, `NowPlayingScreen`.  
- Screens delegate logic to services and hooks for clean separation.  

### **3. Components**
- Reusable UI components: `PlayerControls`, `SongCard`, `AlbumArt`.  
- Keeps screens clean and promotes code reuse.  

### **4. Context / State Management**
- `PlayerContext` manages **global playback state**: current track, playlist, position, shuffle/repeat.  
- Uses `React.createContext` and `useReducer` for predictable state updates.  
- Allows multiple screens to remain synchronized with playback state.  

### **5. Services**
- `AudioService` handles **audio playback** using `expo-av`.  
- `FileService` handles **local music files and playlists**.  
- Keeps all **business logic separate** from UI components.  

### **6. Hooks**
- Custom hooks like `useAudioPlayer` encapsulate playback logic and expose easy-to-use functions to screens/components.  

### **7. Types**
- All important entities are strongly typed:  
  - `Track`: represents a music track with title, artist, URI, artwork, duration.  
  - `Playlist`: collection of tracks.  

---

## Folder Structure
```
Tonica/
│
├─ app/ # App Router screens
│ ├─ _layout.tsx # Tabs layout
│ ├─ index.tsx # Home screen
│ ├─ library.tsx # Library screen
│ ├─ playlists.tsx # Playlists screen
│ └─ now-playing.tsx # Now Playing screen
│
├─ components/ # Reusable UI components
│ ├─ PlayerControls.tsx
│ ├─ SongCard.tsx
│ └─ AlbumArt.tsx
│
├─ context/ # Global state
│ └─ PlayerContext.tsx
│
├─ hooks/ # Custom hooks
│ └─ useAudioPlayer.ts
│
├─ services/ # Business logic
│ ├─ AudioService.ts
│ └─ FileService.ts
│
├─ types/ # TypeScript type definitions
│ ├─ track.ts
│ └─ playlist.ts
│
├─ assets/ # Images, fonts, audio
│ ├─ album_art/
│ ├─ icons/
│ └─ fonts/
│
├─ App.tsx # Entry point
├─ package.json
└─ tsconfig.json

```
---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/your-username/Tonica.git
cd Tonica
```

2. Install dependencies:
```bash
npm install
# or
yarn install
```
3. npx expo start
```bash
npx expo start
```
