
---
Dental_Clinii_WEP – Enterprise Web Edition
Core Purpose
Dental_Clinii_WEP is an enterprise-grade web application designed for comprehensive management of dental clinic operations. It delivers robust business value by streamlining appointment scheduling, patient management, financial tracking, and reporting, all while ensuring data security and operational efficiency. This solution is tailored for clinics seeking a scalable, maintainable, and secure platform to manage both clinical and administrative workflows.
---
Architecture Overview
The solution follows a layered architecture, promoting separation of concerns, maintainability, and testability:
1. Presentation Layer
• ASP.NET MVC: Organizes the UI into Areas (e.g., Admin, Patient, Reception, Public, Doctor) for modularity.
• Controllers: Handle HTTP requests, orchestrate business logic via services, and return views or data.
• ViewModels: Strongly-typed models for passing data between controllers and views.
2. Services Layer
• Business Logic: Encapsulated in service classes (e.g., BookingService, ReportsService, SchedulingService).
• Advanced Features: Handles appointment creation, rescheduling, cancellation, reporting, and notification logic.
• Interfaces: Promote abstraction and facilitate unit testing.
3. Data Access Layer
• Repositories: Implement the Repository Pattern for CRUD operations and domain-specific queries (e.g., AppointmentsRepository, PatientsRepository).
• Unit of Work: Coordinates multiple repositories and manages transactions, ensuring data consistency.
• Entity Framework (Database First): Strongly-typed DbContext (DentistEntities) maps to the underlying SQL Server schema and stored procedures.
4. Models Layer
• EDMX Entities: Auto-generated classes represent database tables and stored procedure results.
• Domain Models: Used throughout the application for business logic and data transfer.
---
Advanced Logic & Features
Appointment Management
• Slot Availability: Ensures no double-booking via conflict checks (HasPatientTimeConflict, HasGlobalTimeConflict).
• Lifecycle Operations: Supports creation, rescheduling, cancellation, and soft deletion of appointments.
• Linking: Appointments can be linked to visits for comprehensive patient tracking.
Financial Tracking
• Payments & Expenses: Tracks service payments, clinic expenses, and calculates daily/weekly revenue and net profit.
• Stored Procedures: Leverages SQL Server stored procedures for financial operations and reporting.
Data Security
• Custom Authorization: Implements a custom AuthorizeAttribute for role-based access control, leveraging encrypted authentication tickets.
• Soft Deletion: Sensitive records (patients, appointments) are soft-deleted to prevent data loss and support auditability.
• Audit Trails: Administrative logins and financial actions are auditable via stored procedures and database triggers. Reporting • Daily/Weekly/Top Services: Aggregates operational and financial statistics for business intelligence. • LINQ & Grouping: Advanced queries for top services, patient statistics, and appointment analytics. --- Technology Stack • .NET Framework 4.7.2 • ASP.NET MVC 5 • Entity Framework 6 (Database First) • SQL Server (with extensive use of stored procedures) • LINQ for data querying and aggregation • DevExpress (if present in UI, for advanced controls and reporting) • jQuery, Bootstrap, Modernizr (bundled for responsive UI) • Custom Security Filters for authentication/authorization --- Design Patterns & Best Practices • Repository Pattern: Abstracts data access logic for each entity, promoting testability and separation of concerns. • Unit of Work Pattern: Manages transactions across multiple repositories, ensuring atomic operations. • Service Layer Pattern: Encapsulates business logic, decoupling it from controllers and data access. • Custom Authorization Attribute: Implements role-based security at the controller/action level. • Soft Delete: Ensures data is not physically removed, supporting audit and recovery. 


--- Solution Structure

Dental_Clinii_WEP/
├── Areas/
│   ├── Admin/
│   ├── Patient/
│   ├── Reception/
│   ├── Doctor/
│   └── Public/
├── Controllers/
├── Core/
│   ├── ViewModels/
│   ├── Constants/
│   └── Enums/
├── Data/
│   ├── Edmx/         # Entity Framework models and stored procedure results
│   ├── Repositories/ # Repository implementations
│   └── UnitOfWork/   # Unit of Work pattern
├── Services/
│   ├── Booking/
│   ├── Scheduling/
│   ├── Reports/
│   └── Notifications/
├── Web/Filters/      # Custom security filters
├── App_Start/        # MVC configuration (routes, bundles, filters)
└── Global.asax       # Application entry point
