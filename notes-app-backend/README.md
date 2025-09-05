# Notes App - React Frontend

A modern, responsive notes application built with React, featuring CRUD operations, note sharing, and a clean UI with TailwindCSS.

## Features

- ✅ **CRUD Operations**: Create, read, update, and delete notes
- ✅ **Note Sharing**: Generate public shareable links for notes
- ✅ **Responsive Design**: Works on desktop, tablet, and mobile devices
- ✅ **Modern UI**: Clean interface built with TailwindCSS
- ✅ **React Router**: Client-side routing for seamless navigation
- ✅ **Context API**: State management for notes
- ✅ **Axios Integration**: HTTP client for API communication
- ✅ **Vercel Ready**: Optimized for Vercel deployment

## Tech Stack

- **React 18** - Frontend framework
- **React Router 6** - Client-side routing
- **TailwindCSS** - Utility-first CSS framework
- **Axios** - HTTP client for API calls
- **Context API** - State management

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Spring Boot backend API running

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd notes-app-frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create environment file:
```bash
cp .env.example .env
```

4. Update the API URL in `.env`:
```env
REACT_APP_API_URL=http://localhost:8080/api
```

5. Start the development server:
```bash
npm start
```

The app will open at `http://localhost:3000`.

### Backend API Requirements

The frontend expects a Spring Boot backend with the following endpoints:

#### Notes API
- `GET /api/notes` - Get all notes
- `GET /api/notes/{id}` - Get note by ID
- `POST /api/notes` - Create new note
- `PUT /api/notes/{id}` - Update note
- `DELETE /api/notes/{id}` - Delete note

#### Sharing API
- `GET /api/notes/share/{id}` - Get shared note (public access)
- `POST /api/notes/{id}/share` - Generate share link

#### Note Data Structure
```json
{
  "id": "string",
  "title": "string",
  "content": "string",
  "createdAt": "datetime",
  "updatedAt": "datetime"
}
```

## Project Structure

```
src/
├── components/          # React components
│   ├── Navbar.js       # Navigation component
│   ├── NotesList.js    # Notes listing component
│   ├── NoteEditor.js   # Note creation/editing component
│   └── NoteViewer.js   # Note viewing component
├── context/            # React Context
│   └── NotesContext.js # Notes state management
├── services/           # API services
│   └── api.js         # Axios configuration and API calls
├── App.js             # Main app component with routing
├── index.js           # App entry point
└── index.css          # Global styles with TailwindCSS
```

## Deployment

### Vercel Deployment

1. Push your code to GitHub
2. Connect your repository to Vercel
3. Set environment variables in Vercel dashboard:
   - `REACT_APP_API_URL`: Your Spring Boot API URL
4. Deploy!

### Manual Build

```bash
npm run build
```

The build files will be in the `build` directory.

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `REACT_APP_API_URL` | Backend API base URL | `http://localhost:8080/api` |

## Features Overview

### Notes Management
- View all notes in a responsive grid layout
- Create new notes with title and content
- Edit existing notes
- Delete notes with confirmation
- Real-time updates and error handling

### Note Sharing
- Generate shareable links for any note
- Public read-only view for shared notes
- Copy share links to clipboard
- Visual indicators for shared notes

### Responsive Design
- Mobile-first approach
- Responsive grid layouts
- Touch-friendly interface
- Optimized for all screen sizes

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License.
