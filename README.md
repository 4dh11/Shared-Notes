# 📝 Shared Notes

**A full-stack, cross-platform note-taking ecosystem featuring a React web client, a native Android mobile app, and a robust Node.js/MongoDB backend.**

## 📖 Overview

Shared Notes is a comprehensive productivity solution designed for seamless synchronization across devices. It combines a modern, responsive frontend built with **React & Vite** with a secure, RESTful backend powered by **Node.js & Express**.

This repository is a **Monorepo** containing both the client and server codebases:
* **`frontend/`**: The web and mobile application (React + Capacitor).
* **`backend/`**: The REST API and database logic (Node.js + MongoDB).

---

## 🚀 Key Features

### 💻 Core Experience
* **Rich Text Editor**: Full markdown support with formatting (bold, lists, headings).
* **Smart Organization**: Pin important notes, search instantly, and manage a "Soft Delete" Trash system.
* **Customization**: Toggle Dark/Light themes and upload custom wallpapers with adjustable dimming.

### 📱 Mobile & Cross-Platform
* **Android Native App**: Built with **Capacitor**, offering a native experience with touch gestures.
* **Responsive Design**: Fluid UI that adapts to desktop, tablet, and mobile screens.
* **Offline Capability**: View cached notes even without an internet connection.

### 🔐 Security & Backend
* **JWT Authentication**: Secure, token-based session management with auto-logout.
* **Soft Deletion**: Notes are moved to a "Trash" bin before permanent deletion (30-day auto-cleanup).
* **Encrypted Data**: Passwords hashed with Bcrypt; secure environment configuration.

---

## 🛠️ Tech Stack

### Frontend (Client)
* **Framework**: React 19.1.0 + Vite 7.0.4
* **Styling**: Tailwind CSS 3.4
* **Mobile Engine**: Capacitor 7.4 (Android)
* **State/Routing**: React Router DOM, Context API
* **HTTP Client**: Axios

### Backend (Server)
* **Runtime**: Node.js
* **Framework**: Express.js
* **Database**: MongoDB (Mongoose ODM)
* **Auth**: JSON Web Tokens (JWT) + Bcrypt
* **File Handling**: Multer (for wallpaper uploads)

---

## 📂 Project Structure

```bash
shared-notes/
├── backend/                # Server-side code
│   ├── src/
│   │   ├── controllers/    # Logic for Notes, Auth, Settings
│   │   ├── models/         # MongoDB Schemas
│   │   └── routes/         # API Endpoints
│   └── uploads/            # Wallpaper storage
│
├── frontend/               # Client-side code
│   ├── android/            # Native Android project files
│   ├── src/
│   │   ├── components/     # React Components
│   │   └── contexts/       # Theme & Auth State
│   └── capacitor.config.json
└── README.md

```

---

## ⚡ Installation & Setup Guide

Since this is a monorepo, you will need to set up the Backend and Frontend separately.

### 1. Clone the Repository

```bash
git clone [https://github.com/4dh11/Shared-Notes.git](https://github.com/4dh11/Shared-Notes.git)
cd Shared-Notes

```

### 2. Backend Setup (The Engine)

Open a terminal and navigate to the backend folder:

```bash
cd backend
npm install

```

**Create a `.env` file in the `backend/` directory with the following content:**

```env
PORT=5001
# Replace <username> and <password> with your actual MongoDB credentials
MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.example.mongodb.net/shared-notes
JWT_SECRET=your_super_secret_key_here
JWT_EXPIRES_IN=7d
# Allow your frontend to talk to the server
FRONTEND_URL_DEV=http://localhost:5173

```

**Start the Server:**

```bash
npm run dev
# Server runs on: http://localhost:5001

```

### 3. Frontend Setup (The UI)

Open a **new** terminal window (keep the backend running) and navigate to the frontend folder:

```bash
cd frontend
npm install

```

**Create a `.env` file in the `frontend/` directory:**

```env
# Point this to your backend URL
VITE_API_URL=http://localhost:5001

```

**Start the Frontend:**

```bash
npm run dev
# App runs on: http://localhost:5173

```

---

## 📱 Mobile Development (Android)

To build the Android application locally:

1. Ensure you have **Android Studio** and the JDK installed.
2. Navigate to the `frontend/` directory.
3. Run the build sequence:
```bash
# 1. Build the React web assets
npm run build

# 2. Sync web assets to the Android native container
npx cap sync android

# 3. Open the project in Android Studio
npx cap open android

```


4. From Android Studio, click the **"Run"** (Play) button to launch the emulator or deploy to a connected device.

---

## 📚 API Reference (Highlights)

| Method | Endpoint | Description | Auth Required |
| --- | --- | --- | --- |
| **POST** | `/api/auth/login` | Login user & receive JWT | ❌ |
| **GET** | `/api/notes` | Get all notes (supports `?q=search`) | ✅ |
| **POST** | `/api/notes` | Create a new note | ✅ |
| **DELETE** | `/api/notes/:id` | Move note to Trash (Soft Delete) | ✅ |
| **GET** | `/api/settings/trash` | View trashed notes | ✅ |
| **POST** | `/api/settings/upload-wallpaper` | Upload custom background | ✅ |

---

## 🚀 Deployment

This project is deployed using **Render** as two separate services:

1. **Backend (Web Service):**
* Root Directory: `backend`
* Build Command: `npm install`
* Start Command: `node src/server.js`


2. **Frontend (Static Site):**
* Root Directory: `frontend`
* Build Command: `npm run build`
* Publish Directory: `dist`



---

## 👨‍💻 Author

**SS Adityaa** - [4dh11](https://github.com/4dh11)

* LinkedIn: [Adityaa SS](https://www.linkedin.com/in/adityaa-ss-30233b2b3/)
* Email: adityaa.sureshbabu@gmail.com

## 📄 License

This project is licensed under the MIT License.

```

```
