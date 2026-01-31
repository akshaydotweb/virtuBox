# Simple Notes App

A basic web application for creating, reading, updating, and deleting notes with user authentication.

## Features

- **User Authentication**: Sign up and login functionality
- **CRUD Operations**: Create, view, edit, and delete notes
- **Input Validation**: Basic validation for usernames and passwords
- **SQLite Database**: Local database to store users and notes

## Tech Stack

- **Backend**: Python Flask
- **Database**: SQLite
- **Frontend**: HTML Templates

## Setup Instructions

### Prerequisites

- Python 3.7 or higher
- pip (Python package manager)

### Installation Steps

1. **Create a virtual environment** (Optional but recommended)
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application**
   ```bash
   python app.py
   ```

5. **Open your browser**
   - Navigate to `http://localhost:5000`

## How to Use

### Sign Up
- Click the "Sign Up" link
- Enter a username (minimum 3 characters)
- Enter a password (minimum 4 characters)
- Submit the form

### Login
- Enter your username and password
- Click "Login"

### Dashboard
- View all your notes
- Click "Create New Note" to add a note
- Click "Edit" to modify a note
- Click "Delete" to remove a note

### Logout
- Click the "Logout" button

## Project Structure

```
notes-app/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── templates/             # HTML templates
│   ├── login.html        # Login page
│   ├── signup.html       # Sign up page
│   ├── dashboard.html    # Notes dashboard
│   ├── create_note.html  # Create note page
│   └── edit_note.html    # Edit note page
├── notes.db              # SQLite database (auto-created)
└── README.md             # This file
```

## Database Schema

### User Table
- `id`: Primary key
- `username`: Unique username
- `password`: Hashed password

### Note Table
- `id`: Primary key
- `title`: Note title
- `content`: Note content
- `user_id`: Foreign key (references User)

## Input Validation

- **Username**: Minimum 3 characters, must be unique
- **Password**: Minimum 4 characters
- **Note Title**: Required, cannot be empty
- **Note Content**: Required, cannot be empty

## Security Notes

- Passwords are hashed using Werkzeug's security functions
- Session-based authentication
- Each user can only edit/delete their own notes

## Troubleshooting

**Issue**: Port 5000 already in use
- Solution: Change the port in `app.py` line at the bottom: `app.run(debug=True, port=5001)`

**Issue**: Database errors
- Solution: Delete `notes.db` and restart the app to recreate the database

## Future Improvements

- Add password reset functionality
- Implement email verification
- Add note categories/tags
- Add rich text editor
- Implement search functionality
