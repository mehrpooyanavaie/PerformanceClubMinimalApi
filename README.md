# FanClub Minimal API – High-Performance CRUD with Dapper & PostgreSQL

This **FanClub Minimal API** project showcases how to build a high-performance .NET 6 (or higher) application using the **Minimal API** approach, **Dapper** as a micro-ORM, and **PostgreSQL** as the database. Although the core functionality revolves around simple CRUD operations for clubs and players, the **primary goal** here is to emphasize **performance, speed**, and the ability to handle **high volumes of requests** efficiently.

---

## Table of Contents
1. [Why This Project?](#why-this-project)
2. [Key Features](#key-features)
3. [Technologies Used](#technologies-used)
   - [Minimal API](#minimal-api)
   - [Dapper (Micro-ORM)](#dapper-micro-orm)
   - [PostgreSQL](#postgresql)
4. [Minimal API vs. Traditional REST in .NET](#minimal-api-vs-traditional-rest-in-net)
5. [Project Structure](#project-structure)
6. [Getting Started](#getting-started)
7. [Usage Examples](#usage-examples)
8. [Who Can Benefit?](#who-can-benefit)
9. [Contact](#contact)

---

## Why This Project?
- **Performance Focus**: By leveraging Minimal API and Dapper, the solution aims to reduce overhead and increase throughput.
- **Scalability**: Ideal for environments where request volume may spike, and efficient resource utilization is crucial.
- **Simplicity**: Showcases straightforward CRUD operations, while highlighting how to optimize speed in .NET.

---

## Key Features
1. **CRUD Operations**: Create, Read, Update, and Delete clubs and players.
2. **Cascade Deletion**: Removing a club automatically deletes its associated players.
3. **Swagger Integration**: Easily test and document the API endpoints.
4. **AutoMapper**: Clean separation between database models and view models.
5. **Micro-ORM (Dapper)**: Fast data access without the overhead of a full ORM.
6. **PostgreSQL**: A robust, open-source relational database with excellent performance.

---

## Technologies Used

### Minimal API
- Introduced in .NET 6, Minimal API streamlines the typical .NET Web API structure.
- Reduces boilerplate code, controllers, and extra layers, leading to faster response times.
- Great for microservices and smaller, focused APIs.

### Dapper (Micro-ORM)
- **Dapper** is a lightweight library for data access, providing direct SQL execution with minimal abstraction.
- Faster than many full-featured ORMs (like Entity Framework Core), especially under high load.
- Offers full control over SQL queries, making it easier to optimize performance.

### PostgreSQL
- A powerful open-source relational database known for its robustness and performance.
- Handles high-volume read/write operations efficiently.
- Offers advanced features (JSONB, window functions, etc.) that can scale with your application needs.

---

## Minimal API vs. Traditional REST in .NET
- **Fewer Layers**: No dedicated controllers or unnecessary middlewares, resulting in quicker routing and response.
- **Performance Gains**: Benchmarks often show a **10%–40% improvement** in throughput, depending on the scenario and server configuration.
- **Simplicity**: Ideal for microservices or lightweight applications that don’t require the full ASP.NET Core MVC overhead.
  
> Note: Exact performance metrics vary based on hardware, configuration, and real-world scenarios. However, Minimal APIs generally outperform traditional controller-based APIs in like-for-like comparisons.

---

## Project Structure

```
FanClubMinimalApi
│   Program.cs
│   appsettings.json
│   appsettings.Development.json
│
├── Models
│   ├── Club.cs
│   └── Player.cs
│
├── ViewModels
│   ├── ClubVm.cs
│   └── PlayerVm.cs
│
├── Dtos
│   ├── ClubPost.cs
│   └── PlayerPost.cs
│
└── Mapping
    └── MappingProfile.cs
```

- **Program.cs**: Main entry point, service configuration, and endpoint definitions.
- **Models**: Database entities (`Club`, `Player`).
- **ViewModels**: Response models to separate database models from API responses.
- **Dtos**: Data Transfer Objects for creating/updating records.
- **MappingProfile.cs**: AutoMapper configuration for mapping between entities and view models.

---

## Getting Started

1. **Prerequisites**:
   - .NET 6 SDK (or higher)
   - PostgreSQL installed (or use Docker)
2. **Database Setup**:
   - Create a new database (e.g., `fanclub`) in PostgreSQL.
   - Run the SQL script you already have (creates tables and seeds initial data).
3. **Configure Connection String**:
   - In `appsettings.json` (or `appsettings.Development.json`), ensure the `"DefaultConnection"` string matches your PostgreSQL setup:
     ```json
     {
       "ConnectionStrings": {
         "DefaultConnection": "Host=localhost;Port=5432;Database=fanclub;Username=postgres;Password=yourpassword"
       }
     }
     ```
4. **Run the Application**:
   - Via command line: `dotnet run`
   - Or use your preferred IDE (Visual Studio, Rider, VS Code).

When the application starts, Swagger UI is available at:
```
https://localhost:<port>/swagger
```

---

## Usage Examples

### Clubs
- **GET** `/get-by-id-club/{id}`  
  Retrieves a specific club with its players.
- **POST** `/add-club`  
  Creates a new club.
- **PUT** `/update-club/{id}`  
  Updates an existing club.
- **DELETE** `/delete-by-id-club-with-cascade/{id}`  
  Deletes a club and all associated players (cascade).

### Players
- **GET** `/get-by-id-player/{id}`  
  Retrieves a specific player and the name of their club.
- **POST** `/add-player`  
  Creates a new player.
- **PUT** `/edit-player/{id}`  
  Updates an existing player.
- **DELETE** `/delete-player/{id}`  
  Deletes a single player.

---

## Who Can Benefit?
- **Backend Developers** looking to learn Minimal APIs in .NET.
- **Performance Enthusiasts** who want to maximize throughput and handle more requests.
- **Developers** who prefer straightforward SQL queries and need more control over query performance.
- **Teams** working on microservices or smaller services that don’t need the full ASP.NET Core MVC structure.

---

## Contact
If you have any questions or need further assistance, feel free to reach out via email:

**[mnavaienezhad@gmail.com]**

---

> **Note**: This project aims to illustrate a high-performance approach with Dapper and Minimal API. For more complex scenarios or enterprise-scale applications, additional layers (e.g., domain services, advanced logging, distributed caching) may be required.
