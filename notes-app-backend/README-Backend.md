# Notes App - Spring Boot Backend

A RESTful API backend for the Notes App built with Spring Boot, featuring CRUD operations, note sharing, and H2 database integration.

## Features

- ✅ **RESTful API**: Complete CRUD operations for notes
- ✅ **JPA/Hibernate**: Database abstraction with H2 in-memory database
- ✅ **Note Sharing**: Public read-only access to shared notes
- ✅ **CORS Support**: Configured for React frontend integration
- ✅ **Global Exception Handling**: Comprehensive error handling
- ✅ **Validation**: Input validation with proper error responses
- ✅ **Docker Support**: Containerized application
- ✅ **Deployment Ready**: Procfile for cloud deployment

## Tech Stack

- **Spring Boot 3.2.0** - Main framework
- **Spring Data JPA** - Data persistence
- **H2 Database** - In-memory database (development)
- **Hibernate** - ORM framework
- **Maven** - Dependency management
- **Docker** - Containerization
- **Jakarta Validation** - Input validation

## API Endpoints

### Notes Management
- `GET /api/notes` - Get all notes (ordered by creation date)
- `GET /api/notes/{id}` - Get note by ID
- `POST /api/notes` - Create a new note
- `PUT /api/notes/{id}` - Update an existing note
- `DELETE /api/notes/{id}` - Delete a note

### Note Sharing
- `GET /api/notes/share/{id}` - Get shared note (public read-only access)

### Statistics
- `GET /api/notes/count` - Get total note count

## Data Models

### Note Entity
```json
{
  "id": 1,
  "title": "Note Title",
  "content": "Note content...",
  "createdAt": "2024-01-01T10:00:00",
  "updatedAt": "2024-01-01T10:00:00"
}
```

### Note Request DTO
```json
{
  "title": "Note Title",
  "content": "Note content..."
}
```

## Getting Started

### Prerequisites
- Java 17 or higher
- Maven 3.6 or higher
- Docker (optional)

### Local Development

1. **Clone the repository:**
```bash
git clone <repository-url>
cd notes-app-backend
```

2. **Run the application:**
```bash
./mvnw spring-boot:run
```

3. **Access the application:**
- API Base URL: `http://localhost:8080/api`
- H2 Console: `http://localhost:8080/h2-console`
  - JDBC URL: `jdbc:h2:mem:notesdb`
  - Username: `sa`
  - Password: `password`

### Docker Deployment

1. **Build the Docker image:**
```bash
docker build -t notes-app-backend .
```

2. **Run the container:**
```bash
docker run -p 8080:8080 notes-app-backend
```

### Cloud Deployment

#### Heroku
1. Create a new Heroku app
2. Add the Heroku Git remote
3. Deploy: `git push heroku main`

#### Railway
1. Connect your GitHub repository
2. Railway will automatically detect the Spring Boot app
3. Deploy with one click

#### Render
1. Connect your GitHub repository
2. Select "Web Service"
3. Build Command: `./mvnw clean package -DskipTests`
4. Start Command: `java -jar target/notes-app-backend-1.0.0.jar`

## API Usage Examples

### Create a Note
```bash
curl -X POST http://localhost:8080/api/notes \
  -H "Content-Type: application/json" \
  -d '{
    "title": "My First Note",
    "content": "This is the content of my note."
  }'
```

### Get All Notes
```bash
curl -X GET http://localhost:8080/api/notes
```

### Get Note by ID
```bash
curl -X GET http://localhost:8080/api/notes/1
```

### Update a Note
```bash
curl -X PUT http://localhost:8080/api/notes/1 \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Updated Note Title",
    "content": "Updated content..."
  }'
```

### Delete a Note
```bash
curl -X DELETE http://localhost:8080/api/notes/1
```

### Get Shared Note
```bash
curl -X GET http://localhost:8080/api/notes/share/1
```

## Configuration

### Database Configuration
The application uses H2 in-memory database by default. To switch to MySQL:

1. Add MySQL dependency to `pom.xml`:
```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```

2. Update `application.properties`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/notesdb
spring.datasource.username=your_username
spring.datasource.password=your_password
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
```

### CORS Configuration
CORS is configured to allow all origins for development. For production, update the CORS configuration in `NoteController.java`:

```java
@CrossOrigin(origins = "https://your-frontend-domain.com", maxAge = 3600)
```

## Error Handling

The API returns standardized error responses:

### 404 - Note Not Found
```json
{
  "status": 404,
  "error": "Note Not Found",
  "message": "Note not found with id: 1",
  "timestamp": "2024-01-01T10:00:00"
}
```

### 400 - Validation Error
```json
{
  "status": 400,
  "error": "Validation Failed",
  "message": "One or more fields have validation errors",
  "timestamp": "2024-01-01T10:00:00",
  "fieldErrors": {
    "title": "Title cannot be blank"
  }
}
```

## Testing

Run the test suite:
```bash
./mvnw test
```

## Project Structure

```
src/main/java/com/notesapp/
├── controller/          # REST controllers
│   └── NoteController.java
├── dto/                # Data Transfer Objects
│   ├── NoteRequest.java
│   └── NoteResponse.java
├── entity/             # JPA entities
│   └── Note.java
├── exception/          # Exception handling
│   ├── GlobalExceptionHandler.java
│   └── NoteNotFoundException.java
├── repository/         # Data repositories
│   └── NoteRepository.java
├── service/            # Business logic
│   └── NoteService.java
└── NotesAppApplication.java
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## License

This project is licensed under the MIT License.
