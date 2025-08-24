# AirBnB Clone Project
The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts

## Project Goals
1. **User Management:** Implement a secure system for user registration, authentication, and profile management.
2. **Property Management:** Develop features for property listing creation, updates, and retrieval.
3. **Booking System:** Create a booking mechanism for users to reserve properties and manage booking details.
4. **Payment Processing:** Integrate a payment system to handle transactions and record payment details.
5. **Review System:** Allow users to leave reviews and ratings for properties.
6. **Data Optimization:** Ensure efficient data retrieval and storage through database optimizations.

## Technology Stack
* **Django:** A high-level Python web framework used for building the RESTful API.
* **Django REST Framework:** Provides tools for creating and managing RESTful APIs.
* **PostgreSQL:** A powerful relational database used for data storage.
* **GraphQL:** Allows for flexible and efficient querying of data.
* **Celery:** For handling asynchronous tasks such as sending notifications or processing payments.
* **Redis:** Used for caching and session management.
* **Docker:** Containerization tool for consistent development and deployment environments.
* **CI/CD Pipelines:** Automated pipelines for testing and deploying code changes.

## Team Roles and Responsibilities
* **Backend Developer:** Responsible for implementing API endpoints, database schemas, and business logic.
* **Frontend Developer:** Designs and builds the visual and interactive parts of a website or web application that users see and interact with directly.
* **Database Administrator:** Manages database design, indexing, and optimizations.
* **DevOps Engineer:** Handles deployment, monitoring, and scaling of the backend services.
* Quality Assurance (QA) Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.
* **Test Automation Engineer:** Designs, develops, and maintains automated testing frameworks and scripts to test software products, ensuring they meet quality and functionality standards.
* **Software Architect Engineer:** Responsible for defining the overall structure and design of a software system.
* **Project Manager (PM):** Responsible for planning, coordinating, and overseeing projects to ensure they are completed on time, within budget, and to the agreed-upon scope and quality standards. 
* **UI/UX Designer:** Creates user-friendly and aesthetically pleasing digital products by focusing on both user experience (UX) and user interface (UI) design.

## Database Design
### Users
**Fields**
- `id`: Unique identifier
- `name`: Full name
- `email`: Email address
- `password`: Hashed password
- `created_at`: Account creation date

**Relationships:**
- A user can **own multiple properties**
- A user can **make multiple bookings**
- A user can **write reviews**

### Properties
**Fields:**
- `id`: Unique property ID
- `owner_id`: References the user who owns the property
- `title`: Name or short description
- `location`: Address or general area
- `price_per_night`: Cost of stay per night

**Relationships:**
- A property is **owned by one user**
- A property can have **multiple bookings**
- A property can receive **multiple reviews**

### Bookings
**Fields:**
- `id`: Unique booking ID
- `user_id`: References the user who made the booking
- `property_id`: References the booked property
- `start_date`: Check-in date
- `end_date`: Check-out date

**Relationships:**
- A booking is **made by one user**
- A booking is **for one property**

### Reviews
**Fields:**
- `id`: Unique review ID
- `user_id`: Who wrote the review
- `property_id`: Which property is being reviewed
- `rating`: Numerical score (e.g., 1–5)
- `comment`: Optional text feedback

**Relationships:**
- A review is **written by one user**
- A review is **for one property**

### Payments
**Fields:**
- `id`: Unique payment ID
- `booking_id`: References the booking being paid for
- `amount`: Total paid
- `status`: Payment status (e.g., completed, pending)
- `payment_date`: Date of payment

**Relationships:**
- A payment is **for one booking**
- A booking can have **one payment**

## Feature Breakdown
1. **User Management:** Allows users to register, log in, and manage their profiles. This system handles authentication, stores user details securely, and controls access to different parts of the application based on user roles (e.g., guest vs. host).
2. **Property Management:** Hosts can list their properties by providing information such as location, description, price, and availability. This feature enables users to browse available accommodations and allows hosts to update or remove listings as needed.
3. **Booking System:** Enables users to book available properties for specific dates. It prevents double-bookings, handles date validations, and ties each reservation to both the user and the property.
4. **Review System:** Lets users leave feedback on properties they’ve stayed in, using a rating and optional comment. Reviews help build trust in the platform and provide valuable insights to future guests.
5. **Payment Processing:** Processes payments for bookings, ensuring secure and trackable transactions. It links each payment to a booking and helps simulate a real-world e-commerce environment within the application.
6. **Database Optimizations:** To ensure performance and scalability, and to improve performance, reduce latency, and ensure the application can scale as the dataset grows.
7. **API Documentation:** The backend APIs are documented using the OpenAPI standard, making them easy to understand and integrate with. The application uses Django REST Framework to provide RESTful endpoints for standard CRUD operations on users, properties, bookings, and reviews. Additionally, GraphQL is implemented to allow more flexible and efficient data queries tailored to client needs.
8. **Search and Filtering:** Allows users to search for properties based on criteria such as location, date, price, and rating. This improves user experience by helping them find suitable listings quickly.

## API Security
1. **Authentication:** All API endpoints require user authentication using token-based methods. This ensures that only verified users can access and interact with protected resources. Authentication is essential for safeguarding personal user information and preventing unauthorized access.
2. **Authorization:** Role-based access control (RBAC) will be used to restrict certain actions based on user roles.
3. **Rate Limiting:** Rate limiting will be applied to prevent abuse such as brute-force attacks or denial-of-service (DoS) attempts. This helps maintain application availability and protects against overloading the server with excessive requests.
4. **Secure Payments:** Payment endpoints will be protected through HTTPS and integrated with secure payment gateways. Securing payment transactions is vital to prevent fraud and protect sensitive financial information.
5. **Data Validation & Sanitization:** All inputs will be validated and sanitized to prevent common vulnerabilities such as SQL injection and cross-site scripting (XSS). This helps ensure only clean, expected data is processed by the application.

## CI/CD Pipeline
**Continuous Integration (CI)** and **Continuous Deployment/Delivery (CD)** are practices that automate the process of testing, building, and deploying code. CI/CD pipelines help ensure that new changes to the codebase are automatically tested and deployed with minimal manual intervention, leading to faster and more reliable development workflows.
For this project, a CI/CD pipeline will:
- Automatically run tests when code is pushed or a pull request is created.
- Build and deploy the application to a staging or production environment.
- Ensure code quality and catch issues early before they reach production.

**Tools Used**
- **GitHub Actions** – For automating workflows such as testing, linting, and deployment.
- **Docker** – For containerizing the application, ensuring consistent environments across development, testing, and production.
- **Hosting Service** – For deploying and hosting the application.
- **Django test suite** – For running automated tests during the CI phase.