# 📝 My Notepad

> A powerful, secure, and offline-first personal notebook application built with modern web technologies and wrapped in Electron for a seamless desktop experience.

<div align="center">
  <!-- Placeholder for a hero screenshot provided by the user -->
  <img src="https://via.placeholder.com/800x450?text=My+Notepad+Dashboard" alt="Dashboard Screenshot" />
</div>

## 📖 Project Description

**My Notepad** is a desktop application designed for local data privacy and ease of use. It combines the flexibility of web technologies (Node.js, Express) with the native feel of a desktop app (Electron). Unlike cloud-based note apps, **My Notepad** stores all your data locally on your machine in a robust SQLite database, ensuring your personal notes and images stay private.

The app features a rich text editor (powered by Quill.js), image support, categorization, and advanced search filtering capabilities, making it perfect for daily journaling, code snippets, or project planning.

## ✨ Key Features

-   **🖥️ Desktop Experience**: Runs as a standalone Windows application.
-   **🔒 Local & Private**: All data is stored locally in `~/notepad-data`, ensuring partial privacy.
-   **🖋️ Rich Text Editing**: Full formatting support (Bold, Italic, Lists) using **Quill.js**, plus image resizing.
-   **🖼️ Image Support**: Upload images directly into notes or embed them in the editor.
-   **📁 Organization**: Categorize notes and filter them instantly.
-   **🔍 Advanced Search**: Search by title, content, or filter by specific date ranges.
-   **⭐ Favorites**: Quickly access your most important notes.
-   **📤 Export to HTML**: One-click export of any note to your Desktop as a standalone HTML file.
-   **⌨️ Productivity Shortcuts**: Use `Ctrl + S` to instantly save your work.

## 🛠️ Tech Stack

### Frontend (Views)
-   **EJS (Embedded JavaScript)**: For server-side rendering of dynamic views.
-   **Quill.js**: A modern, powerful rich text editor.
-   **CSS3**: Custom responsive styling for a clean UI.
-   **FontAwesome**: For UI icons.

### Backend (Logic)
-   **Node.js & Express.js**: Handles application logic, routing, and file serving.
-   **Multer**: Middleware for handling `multipart/form-data` (image uploads).
-   **Moment-timezone**: For accurate date and time formatting (Baghdad Time).

### Database & Storage
-   **SQLite3**: Serverless, zero-configuration SQL database engine.
-   **Local File System**: Stores user uploaded images in the user's home directory.

### DevOps & Distribution
-   **Electron**: Wraps the web app into a native desktop executable.
-   **Electron Builder**: Handles packaging and building the Windows (`.exe`) and other OS installers.

---

## 🚀 Installation

### Option 1: Install from Release (Recommended)
1.  Go to the [Releases](#) page of this repository.
2.  Download the latest installer file (e.g., `My Notepad Setup 1.0.0.exe`).
3.  Run the installer and follow the on-screen instructions.
4.  The app will launch automatically after installation.

### Option 2: Run from Source
If you are a developer and want to modify the app:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/its-ali-hadi/note-pad.git
    cd note-pad
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Run in Development Mode (Browser):**
    This starts only the Express server.
    ```bash
    npm start
    ```
    Access at: `http://localhost:5050`

4.  **Run in Desktop Mode (Electron):**
    This starts the app in a native window.
    ```bash
    npm run electron
    ```

---

## 🏗️ Architecture Overview

The application follows a **Hybrid Desktop Architecture**:

1.  **Main Process (Electron)**:
    -   Starts the Node.js sub-process (`app.js`).
    -   Creates a `BrowserWindow` that loads the local localhost URL.
    -   Manages application lifecycle (startup, shutdown).

2.  **Server Process (Express)**:
    -   Runs locally on port `5050` (or dynamic).
    -   Connects to the SQLite database located at `%USERPROFILE%\notepad-data\notepad.db`.
    -   Serves EJS templates and static assets.
    -   Handles API-like routes for creating and updating notes.

3.  **Data Storage**:
    -   **Database**: stored at `~\notepad-data\notepad.db`.
    -   **Images**: stored at `~\notepad-data\imgs\`.

---

## 🔌 Routes / API Endpoints

Although a local app, it uses REST-like routes internally:

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | Home page with list of notes, search, and filters. |
| `GET` | `/note/:id` | View a single note details. |
| `GET` | `/new` | Form to create a new note. |
| `POST` | `/new` | API to save a new note (Support file upload). |
| `GET` | `/edit/:id` | Form to edit an existing note. |
| `POST` | `/edit/:id` | API to update a note. |
| `POST` | `/delete/:id` | Delete a note and its associated image. |
| `POST` | `/favorite/:id` | Toggle "Favorite" status. |
| `GET` | `/favorites` | View all favorite notes. |

---

## 🛡️ Performance, Security & Scaling

-   **Performance**: The app is lightweight. Using SQLite means there is no heavy database server process running in the background. Content is rendered efficiently using EJS.
-   **Security**:
    -   **Data Ownership**: All data resides on the user's physical machine. Nothing is sent to the cloud.
    -   **Input Validation**: Inputs are sanitized to prevent basic injection attacks.
    -   **File Safety**: Only image mimetypes (`jpeg`, `png`, `gif`, `webp`) are allowed for upload.
-   **Scaling**:
    -   Currently designed for a **single user**.
    -   To scale for multiple users, the database would need to be migrated to a client-server model (e.g., PostgreSQL) and authentication functionality added.

---

## 📸 Screenshots

| Create New Note | View Note |
| :---: | :---: |
| <img src="https://via.placeholder.com/400x300?text=Editor+Interface" alt="soon..." /> | <img src="https://via.placeholder.com/400x300?text=View+Mode" alt="soon..." /> |

| Search & Filter | Light/Dark Mode |
| :---: | :---: |
| <img src="https://via.placeholder.com/400x300?text=Search+Tools" alt="soon..." /> | <img src="https://via.placeholder.com/400x300?text=Theme+Toggle" alt="soon..." /> |

---

## 📂 Project Structure

```bash
notepad-app/
├── dist/                # Electron build artifacts
├── node_modules/        # Dependencies
├── public/              # Static Assets
│   └── style.css        # Main stylesheet
├── views/               # EJS Templates
│   ├── partials/        # Header & Footer
│   ├── index.ejs        # Dashboard
│   ├── new.ejs          # Create Note
│   ├── show.ejs         # Read Note
│   └── ...
├── app.js               # Express Server & DB Logic
├── main.js              # Electron Main Process
├── package.json         # Config & Scripts
└── ...
```

---

<div align="center">

**Made with ❤️ using Node.js & Electron**

</div>
