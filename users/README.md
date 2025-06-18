# Users Directory

This directory contains all user data for the Bolt AI application.

## Structure

```
users/
├── users.json              # List of all registered users
├── user_[ID]/              # Individual user directories
│   ├── profile.json        # User profile information
│   └── userdata.json       # Complete user data (chats, settings, tokens)
└── README.md               # This file
```

## File Descriptions

### users.json
Contains an array of all registered users with their basic information:
- id: Unique user identifier
- username: User's chosen username
- email: User's email address
- createdAt: Account creation timestamp
- lastLogin: Last login timestamp
- password: User's password (in production, this should be hashed)

### profile.json
Individual user profile data containing the same information as in users.json.

### userdata.json
Complete user data structure:
```json
{
  "profile": { /* user profile data */ },
  "chats": [ /* array of user's chat conversations */ ],
  "settings": {
    "theme": "dark",
    "language": "en",
    "notifications": true
  },
  "tokens": {
    "hourlyTokensUsed": 0,
    "lastResetHour": "2025-06-18T17:00:00.000Z"
  }
}
```

## Security Notes

- Passwords are currently stored in plain text (for demo purposes)
- In production, implement proper password hashing (bcrypt, argon2, etc.)
- Consider encrypting sensitive user data
- Implement proper access controls and validation

## Usage

The UserService class handles all file operations:
- Creating new users
- Authenticating users
- Updating user data
- Managing user sessions
- Storing chat history
- Tracking token usage

## Backup

This directory should be backed up regularly to preserve user data.
Consider implementing automatic backups and data recovery procedures. 