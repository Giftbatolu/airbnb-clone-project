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