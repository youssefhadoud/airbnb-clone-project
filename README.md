# airbnb-clone-project
======================
Team Roles
1. Project Manager (PM)
Brief:
Manages project execution, team coordination, and ensures delivery within scope, time, and budget.

Detailed:

Distributes tasks, manages timelines, and motivates the team.

In Agile, promotes transparency, communication, and continuous improvement.

Bridges the gap between stakeholder expectations and team execution.

2. Business Analyst (BA)
Brief:
Analyzes business needs and translates them into technical requirements for the team.

Detailed:

Understands customer workflows and dives into business processes.

Converts an abstract product vision into concrete, actionable requirements.

Bridges communication between the client and the development team.

3. Product Owner (PO)
Brief:
Defines the product vision, manages the backlog, and ensures the product meets business goals.

Detailed:

Balances market trends and customer needs.

Maintains the product backlog and prioritizes features.

Works closely with stakeholders to deliver maximum business value.

4. UI/UX Designer
Brief:
Designs intuitive, user-friendly interfaces and creates excellent user experiences.

Detailed:

Designs visually appealing interfaces (UI) and user journeys (UX).

Conducts user research, creates personas, wireframes, and prototypes.

Continuously improves the user experience based on feedback and metrics.

5. Software Architect
Brief:
Plans the high-level technical architecture and technology stack for the application.

Detailed:

Designs software structures and makes key technical decisions.

Selects tools, frameworks, and sets code quality standards.

Ensures security, scalability, and integration strategies.

6. Software Developer
Brief:
Builds and maintains the core functionality of the application.

Detailed:

Frontend developers handle UI and user interactions.

Backend developers implement business logic, algorithms, and databases.

Full-stack developers manage both frontend and backend development.

7. Quality Assurance (QA) Engineer
Brief:
Tests the application to ensure it meets functional and non-functional requirements.

Detailed:

Conducts different types of testing (functional, usability, security, performance).

Reports defects and ensures overall application quality.

Develops and manages testing documentation like test cases and test reports.

8. Test Automation Engineer
Brief:
Automates testing to improve efficiency and reliability.

Detailed:

Writes scripts for automated testing.

Designs easy-to-maintain automation frameworks.

Identifies what to automate and what to test manually.

9. DevOps Engineer
Brief:
Automates software delivery and infrastructure operations.

Detailed:

Builds and manages CI/CD pipelines.

Unifies development and operations for faster and safer deployments.

Oversees releases, infrastructure, and system stability.

====================
 Technology Stack

This section outlines the technologies used in the Airbnb Clone backend and their specific roles in the project.

1- Django 
  Acts as the core backend framework responsible for handling business logic, routing requests, and defining models for users, properties, bookings, payments, and reviews.

2- Django REST Framework (DRF)
  Used to build RESTful API endpoints that power the frontend of the Airbnb Clone. It manages all HTTP-based interactions like registering users, creating listings, or processing bookings.

3- PostgreSQL
  Stores all relational data such as user profiles, property details, bookings, payments, and reviews. Ensures data integrity and supports complex queries efficiently.

4- GraphQL
  Enables clients to request exactly the data they need (e.g., a property with only specific fields). It is especially useful for frontend performance and dynamic UIs by reducing over-fetching.

5- Celery 
  Handles background tasks like sending email confirmations, processing delayed payments, or notifying users of booking updates without blocking the main application flow.

6- Redis  
  Supports fast in-memory caching to store frequently accessed data like property details or session tokens. Also acts as a message broker for Celery to process asynchronous tasks.

7- Docker 
  Ensures that the development and production environments are consistent by containerizing the backend, PostgreSQL, Redis, and other services used in the project.

8- CI/CD Pipelines
  Automatically tests and deploys code whenever changes are pushed to the repository, ensuring stable and continuous delivery of new features and bug fixes.

  ===========
   Database Design

This section outlines the core database entities used in the Airbnb Clone backend, including their key fields and relationships.

 Users
Represents individuals using the platform as either guests or hosts.

Key Fields:
- id: Unique identifier
- username: User's login name
- email: Contact email and login email
- password: Hashed password for authentication
- role: Specifies if the user is a host or guest

Relationships:
- A user can create multiple property listings (if they are a host)
- A user can make multiple bookings (if they are a guest)
- A user can write multiple reviews

---

 Properties
Represents a listing available for booking on the platform.

Key Fields:
- id: Unique identifier
- title: Name of the property
- -images: images for the proerty
- description: Description of the property
- location: Address or geographical location
- price_per_night: Cost per night of stay

Relationships:
- A property is created by a user (host)
- A property can have multiple bookings
- A property can have multiple reviews

---

Bookings
Represents a reservation made by a guest for a property.

Key Fields:
- id: Unique identifier
- user_id: References the user who made the booking
- property_id: References the booked property
- check_in: Start date of the booking
- check_out: End date of the booking

Relationships:
- A booking belongs to one user
- A booking is linked to one property
- A booking may trigger one or more payment records

---

Payments
Tracks the payment transactions made for bookings.

Key Fields:
- id: Unique identifier
- booking_id: References the related booking
- amount: Total amount paid
- payment_status: Status (e.g., pending, completed)
- payment_date: Timestamp of payment

Relationships:
- A payment is associated with a single booking

---

 Reviews
Captures user feedback and ratings for properties.

Key Fields:
- id: Unique identifier
- user_id: References the reviewer
- property_id: References the property being reviewed
- rating: Numeric rating (e.g., 1 to 5 stars)
- comment: Written feedback

Relationships:
- A review is written by a user
- A review is linked to a specific property

