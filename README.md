# Airbnb Clone Project

## Overview

The **Airbnb Clone Project** is a full-stack web application that replicates key features of Airbnb, with a primary focus on backend systems. It is designed to provide hands-on experience in backend architecture, database design, API development, and application security, simulating a real-world software engineering environment.

## Project Goals

- Develop a scalable booking platform backend using modern technologies.
- Design and implement a relational database structure that mirrors real-world lodging and user interactions.
- Build secure, RESTful and GraphQL APIs.
- Integrate CI/CD pipelines for continuous testing, building, and deployment.
- Practice collaborative development workflows using GitHub and industry best practices.

## Tech Stack

- **Backend Framework:** Django (Python)
- **Database:** MySQL
- **API Design:** REST & GraphQL
- **Containerization:** Docker
- **Version Control:** Git + GitHub
- **CI/CD:** GitHub Actions
- **Project Management:** GitHub Projects / Issues

## Key Features

- User Authentication and Authorization
- Property Listings and Bookings
- Search and Filter Functionality
- Payment Integration (planned)
- Admin Panel and User Roles
- API Rate Limiting and Security

---

> This repository is the foundation for a real-world clone project as inititated by ALx. Each stage of development will be documented with commits and supporting markdown files for clarity and collaboration.

## Team Roles

In a real-world software engineering environment, collaboration across specialised roles ensures product quality, timely delivery, and scalability. Below are the key roles involved in the Airbnb Clone project:

### Business Analyst
Gathers and defines business requirements from stakeholders, ensuring that the development team builds features aligned with user and business goals.

### Product Owner
Owns the product vision and roadmap. Prioritises features based on business value, manages the product backlog, and serves as the liaison between stakeholders and the development team.

### Project Manager
Oversees the project timeline, resource allocation, and team coordination. Ensures deliverables meet deadlines and communicates progress or blockers to stakeholders.

### UI/UX Designer
Designs user interfaces and experiences that are intuitive, accessible, and visually appealing. Converts business needs into design mockups, wireframes, and user flows.

### Software Architect
Defines the high-level structure of the application. Makes key decisions around system design, technology stack, and scalability to ensure technical alignment with business needs.

### Software Developer
- **Backend Developer:** Implements the core application logic, API endpoints, database interactions, and security protocols.
- **Frontend Developer:** (if applicable) Builds and integrates user-facing components based on UI/UX designs.

### Quality Assurance (QA) Engineer
Tests the application manually to catch bugs, verify functionality, and ensure usability across different user scenarios.

### Test Automation Engineer
Writes automated test scripts to validate system behaviours continuously. Improves test coverage, efficiency, and regression prevention during deployments.

### DevOps Engineer
Sets up and maintains the CI/CD pipelines. Manages infrastructure, automates deployments, and ensures system stability in production and staging environments.

---

> Each role contributes uniquely to the success of the project. Clear communication and well-defined responsibilities foster collaboration and accelerate progress.

## Technology Stack

This project integrates several modern technologies to create a scalable, maintainable, and secure booking platform. Each technology serves a specific role in the architecture:

### Django
A high-level Python web framework used to build the backend of the application. Handles routing, business logic, authentication, and ORM-based interactions with the database.

### MySQL
A relational database management system used to store and manage structured data such as user information, property listings, bookings, and payments.

### GraphQL
A query language for APIs that allows clients to request exactly the data they need. Enhances flexibility and performance over traditional REST endpoints, especially in complex UIs.

### Docker
A containerisation platform that packages the application and its dependencies into isolated environments. Ensures consistency across development, testing, and production.

### Git & GitHub
Used for version control and team collaboration. GitHub hosts the repository, tracks issues, manages pull requests, and supports CI/CD through GitHub Actions.

### GitHub Actions
A CI/CD tool that automates testing, building, and deployment workflows. Ensures early detection of bugs and consistent delivery pipelines.

### REST (via Django REST Framework)
Provides standardised HTTP-based APIs for interacting with the application, particularly useful for mobile and third-party integrations.

### HTML/CSS/JavaScript (Planned Frontend)
Although this phase focuses on backend, the frontend will be powered by standard web technologies or a frontend framework, consuming the APIs built in Django/GraphQL.

---

> This diverse stack reflects industry-standard tooling and encourages modular, maintainable development practices.

## Database Design

The Airbnb Clone project relies on a relational database structure to manage user activity, property listings, transactions, and reviews. Below are the core entities and their relationships:

### Entities and Fields

#### 1. User
- `id` (Primary Key)
- `name`
- `email`
- `password_hash`
- `role` (guest or host)

Users can either host properties or make bookings as guests.

#### 2. Property
- `id` (Primary Key)
- `host_id` (Foreign Key to User)
- `title`
- `description`
- `location`
- `price_per_night`

Each property is owned by a user (host). A host can own multiple properties.

#### 3. Booking
- `id` (Primary Key)
- `user_id` (Foreign Key to User)
- `property_id` (Foreign Key to Property)
- `check_in_date`
- `check_out_date`
- `total_price`

A booking connects a guest with a property for a specific date range. Each booking belongs to one user and one property.

#### 4. Review
- `id` (Primary Key)
- `user_id` (Foreign Key to User)
- `property_id` (Foreign Key to Property)
- `rating` (1–5)
- `comment`

A user can leave a review for a property after a booking. Each property can have multiple reviews.

#### 5. Payment
- `id` (Primary Key)
- `booking_id` (Foreign Key to Booking)
- `amount`
- `payment_method`
- `status` (e.g., pending, completed)

Each payment is tied to a booking and records transaction details.

### Entity Relationships

- A **User** (as host) can own many **Properties**.
- A **User** (as guest) can make multiple **Bookings**.
- A **Property** can have many **Bookings** and **Reviews**.
- A **Booking** is associated with one **User**, one **Property**, and one **Payment**.
- A **Review** is tied to one **User** and one **Property**.
- A **Payment** is made per **Booking**.

---

> This structure supports essential features like property listings, reservations, user feedback, and payment processing, and can be extended with availability calendars, messaging, and notifications.

## Feature Breakdown

The Airbnb Clone project is feature-driven, focusing on replicating core functionalities of a real-world booking platform. Below are the key features implemented and planned for the application:

### 1. User Management
Handles user registration, authentication, and role assignment (guest or host). This feature ensures that only authorised users can access or manage specific resources, forming the backbone of a secure, personalised experience.

### 2. Property Management
Enables hosts to list, update, and delete properties. Properties include details such as location, pricing, and descriptions. This feature allows the platform to manage listings effectively and gives hosts control over their offerings.

### 3. Booking System
Allows guests to book properties for specific dates and see availability in real-time. It includes check-in/check-out handling, booking validation, and total price calculation. This ensures a smooth, conflict-free reservation process.

### 4. Review and Rating System
Enables guests to leave feedback after their stay. Hosts and future guests can view ratings and comments, promoting transparency and trust within the platform.

### 5. Payment Processing
Handles transaction recording for bookings. Although integration with real payment gateways is optional at this stage, the system captures payment status, method, and amount for each booking, simulating real-world financial flows.

### 6. API Development (REST & GraphQL)
Exposes core functionality through secure APIs, allowing external services and frontend clients to interact with the platform. GraphQL is used for flexible queries, while REST supports standardised resource access.

### 7. API Security
Implements best practices such as authentication tokens, rate limiting, and data validation to protect user data and prevent misuse of the system. This is critical for maintaining trust and system integrity.

### 8. CI/CD Pipeline Integration
Automates the building, testing, and deployment of the application using GitHub Actions and Docker. This ensures code quality and accelerates development through continuous feedback and faster release cycles.

---

> These features not only reflect common use cases in booking platforms but also demonstrate the integration of software engineering principles like scalability, modularity, and maintainability.


## API Security

Securing the backend APIs is critical to protecting user data, preventing abuse, and maintaining the integrity of the platform. Below are the core security measures implemented in this project:

### 1. Authentication
Users must log in to access protected endpoints. Authentication is handled via secure tokens (e.g., JWT), ensuring only verified users can interact with the system. This prevents unauthorised access to sensitive features like booking and property management.

### 2. Authorization
Different users have different permissions — for example, only a host can edit their own property, and only a guest can make a booking. Role-based access control (RBAC) ensures users can only perform actions appropriate to their role.

### 3. Input Validation and Sanitization
All incoming data is validated and sanitized to prevent SQL injection, XSS (cross-site scripting), and other common web vulnerabilities. This protects the backend and database from malicious payloads.

### 4. Rate Limiting
Limits the number of requests a user or IP can make in a short period. This helps prevent brute-force attacks, API abuse, and denial-of-service scenarios, especially during authentication or payment processing.

### 5. Secure Payment Data Handling
While this project may use simulated payment systems, it still ensures that sensitive payment-related information is handled carefully. Payment records are stored securely and follow best practices, even in sandboxed mode.

### 6. HTTPS and Data Encryption (Planned)
In deployment, HTTPS will be enforced to encrypt all data between the client and server. This prevents man-in-the-middle attacks and secures user sessions.

---

> Security is not optional. It’s a foundational requirement to protect user trust, ensure platform stability, and comply with good engineering and ethical standards.
