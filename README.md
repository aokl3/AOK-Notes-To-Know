# AOK-Notes-To-Know
A Notes Management Application with user authentication, tags, and search functionality.

**AOK Notes to Know** is a Notes Management Application that allows users to create, update, and manage personal notes with features like tagging, searching, and filtering. 

---

## Features
- **User Registration and Authentication**: Securely register and log in users.
- **Personal Notes Management**: Create, update, view, and delete notes.
- **Tags for Categorization**: Use tags to organize notes effectively.
- **Search and Filter**: Quickly find notes based on tags or keywords.

---

## Project Structure
- **`app/models.py`**: Defines the database schema for users and notes.
- **`app/routes/`**: Contains the API endpoints for user authentication and notes management.
- **`Dockerfile`**: Docker configuration to containerize the application.
- **`docker-compose.yml`**: Configuration for setting up the application with a database.

---

## Database Schema

### Users Table
| Column Name  | Data Type | Constraints       |
|--------------|-----------|-------------------|
| `id`         | Integer   | Primary Key       |
| `username`   | String    | Unique, Required  |
| `email`      | String    | Unique, Required  |
| `password`   | String    | Hashed, Required  |

### Notes Table
| Column Name  | Data Type | Constraints                   |
|--------------|-----------|-------------------------------|
| `id`         | Integer   | Primary Key                   |
| `user_id`    | Integer   | Foreign Key (to Users table)  |
| `title`      | String    | Required                      |
| `content`    | Text      |                               |
| `tags`       | String    | Optional (Comma-separated)    |
| `created_at` | Timestamp | Default: current timestamp    |
| `updated_at` | Timestamp | Updated when the note changes |

---

## API Endpoints

### Authentication
- `POST /api/auth/register`: Register a new user.
- `POST /api/auth/login`: Authenticate and log in a user.
- `POST /api/auth/logout`: Log out the user.

### Notes
- `GET /api/notes`: Fetch all notes for the authenticated user.
- `POST /api/notes`: Create a new note.
- `GET /api/notes/{note_id}`: Retrieve a specific note by ID.
- `PUT /api/notes/{note_id}`: Update a note.
- `DELETE /api/notes/{note_id}`: Delete a note.
- `GET /api/notes?tag=work`: Filter notes by a specific tag.
- `GET /api/notes?search=meeting`: Search notes by a keyword.

---

## Docker Instructions
### Build and Run the Application
1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-username/AOK-Notes-To-Know.git
    cd AOK-Notes-To-Know
    ```

2. **Build the Docker image**:
    ```bash
    docker-compose up --build
    ```

3. **Access the application**:
    Visit `http://localhost:5000` in your browser.

---

## Technologies Used
- **Backend**: Flask
- **Database**: PostgreSQL
- **Authentication**: JWT
- **Containerization**: Docker


## Running Tests

To run the tests, make sure you have all dependencies installed and use `pytest`:

```bash
pip install -r requirements.txt
pytest tests/
