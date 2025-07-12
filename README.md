# Student API – SRE Bootcamp Project

This project is a **Student CRUD REST API** built using **Python** and **Flask**, created as part of an SRE Bootcamp exercise to demonstrate key backend development and infrastructure engineering skills.

---

## Project Goals

- Learn REST API design best practices.
- Implement the **Twelve-Factor App** methodology.
- Gain experience with database schema migrations and environment-based configuration.
- Provide production-ready features like versioning, healthchecks, and logging.
- Prepare the project for cloud deployment and infrastructure automation.

---

## Functional Requirements

The API supports the following operations:

- **Add** a new student  
- **Get all** students  
- **Get** a student by ID  
- **Update** an existing student  
- **Delete** a student  

Additionally:

- API must be versioned (e.g. `/api/v1/students`)
- All configurations (e.g., database URL) must be passed via environment variables
- Should expose a `/healthcheck` endpoint
- Proper use of HTTP methods (GET, POST, PUT, DELETE)
- Emit structured logs
- Include unit tests
- Provide a Postman collection
- Database schema should be applied via migrations
- Code must include a `Makefile` to simplify build/run/test operations

---

## Project Structure

```plaintext
student-api/
├── app/
│   ├── models.py
│   ├── db.py
│   ├── __init__.py
│   ├── routes/
│   └── services/
├── tests/
│   └── test_students.py
├── migrations/
├── run.py
├── .env
├── config.py
├── requirements.txt
├── Makefile
├── postman_collection.json
├── README.md
└── terraform/
```

---

## Setup Instructions

1. Clone the Repository
```
git clone https://github.com/YOUR_USERNAME/student-api.git
cd student-api
```

2. Create a Virtual Environment
```
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

3. Install Dependencies
```
pip install -r requirements.txt
```

4. Configure Environment Variables

Create a `.env` file in the root directory:
```
DATABASE_URL=sqlite:///students.db
```

5. Apply Database Migrations
```
make migrate
make upgrade
```
This will generate and apply the database schema using Flask-Migrate.


6. Run the Server
```
make run
```

The API will be available at:
http://localhost:5000/api/v1/students


---

## API Endpoints

| Method | Endpoint                | Description         |
| ------ | ----------------------- | ------------------- |
| GET    | `/api/v1/students`      | Get all students    |
| GET    | `/api/v1/students/<id>` | Get student by ID   |
| POST   | `/api/v1/students`      | Add a new student   |
| PUT    | `/api/v1/students/<id>` | Update student info |
| DELETE | `/api/v1/students/<id>` | Delete a student    |
| GET    | `/healthcheck`          | Health check        |


---

## Run Tests
```
make test
```

---

## Postman Collection
Import the postman_collection.json file in Postman to test all endpoints easily.

---

## Makefile Commands

| Command        | Description                        |
| -------------- | ---------------------------------- |
| `make run`     | Start the Flask development server |
| `make migrate` | Create a new database migration    |
| `make upgrade` | Apply database migrations          |
| `make test`    | Run unit tests                     |
| `make lint`    | Run code linting (optional)        |


---


## Twelve-Factor App Compliance

| Principle              | Implementation                                   |
| ---------------------- | ------------------------------------------------ |
| I. Codebase            | Version-controlled Git repo                      |
| II. Dependencies       | Defined in `requirements.txt`                    |
| III. Config            | `.env` file with environment variables           |
| IV. Backing services   | Uses SQLAlchemy for database abstraction         |
| V. Build, release, run | Separated via Makefile and migrations            |
| VI. Processes          | Stateless Flask app                              |
| VII. Port binding      | Flask binds to port via `app.run()`              |
| VIII. Concurrency      | WSGI-compatible for production (e.g., Gunicorn)  |
| IX. Disposability      | Fast boot/shutdown via lightweight Flask process |
| X. Dev/prod parity     | Works locally and on cloud infra                 |
| XI. Logs               | `logging` module support (can be extended)       |
| XII. Admin tasks       | Database migration and tests via Makefile        |


---


## Next Steps (Optional)
- Containerize with Docker
- Deploy to AWS using Terraform and ECS/Fargate
- Add CI/CD pipeline with GitHub Actions
- Add request-level logging and tracing (e.g., OpenTelemetry)

---

## License

This project is licensed under the MIT License.

---

## Author

Timothy Keaveny - [@harlemtraveler](https://github.com/harlemtraveler)


---

## Citation & Reference

[One2N - SRE Bootcamp - Create a simple REST API Webserver](https://one2n.io/sre-bootcamp/sre-bootcamp-exercises/1-create-a-simple-rest-api)