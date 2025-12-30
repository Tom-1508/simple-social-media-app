# Project-1: FastAPI Photo Sharing Application

A full-stack photo sharing and social application built with FastAPI, featuring user authentication, image uploads, and database management.

## 🚀 Features

- **User Authentication** - JWT-based authentication with email verification and password reset
- **Photo Uploads** - Upload and manage photos with captions using ImageKit
- **User Management** - Create accounts, update profiles, and manage user settings
- **Database** - SQLAlchemy ORM with async SQLite support
- **Modern API** - FastAPI with automatic OpenAPI/Swagger documentation
- **Frontend** - Streamlit-based web interface for easy interaction

## 📋 Prerequisites

- Python 3.12 or higher
- Git
- A personal ImageKit account (for image uploads)

## 🛠️ Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/Project-1.git
   cd Project-1
   ```

2. **Create and activate virtual environment**

   ```bash
   python -m venv .venv
   # On Windows
   .venv\Scripts\activate
   # On macOS/Linux
   source .venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -e .
   ```

   Or if using `uv`:

   ```bash
   uv sync
   ```

4. **Configure environment variables**
   Create a `.env` file in the root directory with your ImageKit credentials:
   ```
   IMAGEKIT_PUBLIC_KEY=your_public_key
   IMAGEKIT_PRIVATE_KEY=your_private_key
   IMAGEKIT_URL_ENDPOINT=your_url_endpoint
   ```

## 🚀 Running the Application

### Start the FastAPI Backend

```bash
python main.py
```

The API will be available at `http://127.0.0.1:8000`

Access the interactive API documentation:

- **Swagger UI**: http://127.0.0.1:8000/docs
- **ReDoc**: http://127.0.0.1:8000/redoc

### Start the Streamlit Frontend

```bash
streamlit run frontend.py
```

The frontend will open in your browser at `http://localhost:8501`

## 📁 Project Structure

```
Project-1/
├── main.py              # Entry point for FastAPI application
├── frontend.py          # Streamlit frontend application
├── pyproject.toml       # Project configuration and dependencies
├── README.md            # This file
├── .env                 # Environment variables (create this)
├── test.db              # SQLite database file
└── app/
    ├── app.py           # FastAPI application setup and routes
    ├── db.py            # Database models and session management
    ├── schemas.py       # Pydantic models for request/response validation
    ├── users.py         # User authentication and authorization
    ├── images.py        # ImageKit integration for photo uploads
    └── __pycache__/     # Python cache
```

## 🔑 API Endpoints

### Authentication

- `POST /auth/register` - Register a new user
- `POST /auth/jwt/login` - Login with email and password
- `POST /auth/request-verify-token` - Request email verification
- `POST /auth/verify` - Verify email address
- `POST /auth/forgot-password` - Request password reset

### Users

- `GET /users/me` - Get current user profile
- `PATCH /users/{id}` - Update user profile
- `GET /users/{id}` - Get user by ID

### Posts

- `POST /upload` - Upload a new photo with caption
- `GET /posts` - Get all posts
- `GET /posts/{id}` - Get post by ID
- `DELETE /posts/{id}` - Delete a post

## 🔧 Technologies Used

- **Framework**: FastAPI
- **Authentication**: FastAPI-Users with JWT
- **Database**: SQLAlchemy + SQLite
- **Image Storage**: ImageKit
- **Frontend**: Streamlit
- **Server**: Uvicorn
- **Validation**: Pydantic

## 📝 Environment Variables

Create a `.env` file with the following variables:

```
# ImageKit Configuration
IMAGEKIT_PUBLIC_KEY=your_imagekit_public_key
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
IMAGEKIT_URL_ENDPOINT=your_imagekit_url_endpoint

# Optional: Database configuration
DATABASE_URL=sqlite+aiosqlite:///./test.db
```

## 🤝 Contributing

Feel free to fork this project and submit pull requests for any improvements!

## 📄 License

This project is open source and available under the MIT License.

## 💡 Notes

- The application uses SQLite for development. For production, consider using PostgreSQL
- Make sure to keep your `.env` file secret and never commit it to version control
- The `.gitignore` file is already configured to exclude sensitive files

## 🆘 Troubleshooting

### Port already in use

If port 8000 is already in use, modify `main.py`:

```python
uvicorn.run("app.app:app", host="127.0.0.1", port=8001, reload=True)
```

### ImageKit errors

Verify your ImageKit credentials are correctly set in the `.env` file

### Database errors

Delete `test.db` to reset the database:

```bash
rm test.db
```

---

**Happy coding!** 🎉
