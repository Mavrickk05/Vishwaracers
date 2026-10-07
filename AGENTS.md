# Vishwaracers Engineering Platform

## Purpose

Vishwaracers is an internal engineering and team-management platform for a Formula Student team.

The application must manage engineering knowledge, vehicle development, testing, team activities, inventory, historical vehicles, rules, and vehicle telemetry.

---

# Engineering Domains

The vehicle is divided into 8 primary domains:

1. Aerodynamics
2. Brakes
3. Chassis
4. Drivetrain
5. Electronics
6. Powertrain
7. Vehicle Software
8. Vehicle Dynamics

These domains must be first-class objects in the database and application.

---

# Highest Priority Feature

## Vehicle Changes

The Home screen must prioritize ongoing vehicle changes.

A vehicle change can contain:

- Vehicle
- Engineering domain
- Component/system
- Change description
- Reason for change
- Member who made/reported it
- Date/time
- Photos
- Documents
- Related task
- Related test
- Previous state
- New state
- Status
- Comments

Vehicle changes must be traceable and searchable.

Fast data entry during physical vehicle testing is a core requirement.

---

# Major Modules

The application must eventually contain:

1. Dashboard
2. Vehicle Changes
3. Vehicles
4. Engineering Domains
5. Tasks
6. Testing
7. Inventory
8. Documents
9. Syllabus
10. Rulebook
11. Members
12. Attendance
13. Historical Cars
14. CAN Telemetry
15. Analytics
16. Settings

---

# Historical Vehicles

Every previous Vishwaracers vehicle must be stored.

Each historical vehicle should contain:

- Vehicle information
- Design information
- Components
- Engineering data
- Testing data
- Documents
- Photos
- Changes
- Lessons learned
- Domain-specific information

Historical data must remain separate from the current vehicle while remaining searchable.

---

# Team Management

Every team member must have:

- Unique member ID
- Name
- Username
- Password authentication
- Role
- Engineering domain
- Profile
- Attendance records
- Tasks
- Contributions/vehicle changes

Use role-based permissions.

---

# Tasks

Tasks can be:

- Technical
- Non-technical

Tasks should support:

- Assignment
- Domain
- Priority
- Status
- Deadline
- Description
- Attachments
- Related vehicle
- Related component
- Related vehicle change
- Comments

---

# Inventory

Inventory must support:

- Parts
- Consumables
- Tools
- Quantity
- Minimum stock
- Location
- Supplier
- Part number
- Cost
- Vehicle association
- Domain association
- Purchase information
- Stock history

---

# Testing

Testing must support rapid data entry while physically working on the car.

A test record should support:

- Vehicle
- Driver
- Test type
- Date/time
- Location
- Conditions
- Setup
- Observations
- Measurements
- Problems
- Photos
- Results
- Related vehicle changes
- Related tasks

The application should eventually support offline-first test entry.

---

# Syllabus

The syllabus section should contain educational information for new members.

It should explain:

- Components
- Systems
- Engineering principles
- Vehicle architecture
- Domain-specific knowledge
- Procedures

---

# Rulebook

The rulebook section should organize competition rules by engineering domain.

Rules should be linkable to:

- Components
- Designs
- Vehicle changes
- Documents
- Tests

---

# CAN Telemetry

Vehicle telemetry will eventually be integrated.

Architecture:

Vehicle ECU/Sensors
        ↓
Vehicle CAN
        ↓
Telemetry ECU
        ↓
SD Card + Wireless
        ↓
Local Server
        ↓
Database
        ↓
Web/Mobile Dashboard

The application must NOT directly control vehicle actuators.

Vehicle telemetry from the application is read-only.

Local SD logging should remain the authoritative vehicle data source.

---

# Technology

## Frontend

- Next.js
- TypeScript
- Tailwind CSS
- shadcn/ui

## Backend

- Python
- FastAPI

## Database

- PostgreSQL

Use database migrations.

## Deployment

The system must eventually run on:

- Development laptop
- Raspberry Pi
- Local team network

Use Docker where practical.

---

# Architecture Rules

1. Keep frontend and backend separated.
2. Use typed API contracts.
3. Validate all backend input.
4. Use database migrations.
5. Do not duplicate business logic unnecessarily.
6. Do not create unnecessary abstractions.
7. Do not modify unrelated modules when implementing a feature.
8. Do not delete working functionality without explicit approval.
9. Keep engineering data traceable.
10. Prefer simple maintainable solutions over premature complexity.
11. Design the database so historical engineering data is preserved.
12. Security and permissions must be enforced by the backend, not only the frontend.
13. Never store plaintext passwords.
14. Never hardcode secrets.
15. Never implement remote vehicle control through the application.

---

# Development Process

Do not build the entire application at once.

Build incrementally.

Recommended order:

1. Architecture
2. Database
3. Authentication
4. Members and roles
5. Vehicles
6. Engineering domains
7. Vehicle Changes
8. Tasks
9. Inventory
10. Documents
11. Testing
12. Historical vehicles
13. Syllabus
14. Rulebook
15. CAN telemetry
16. Analytics
17. Raspberry Pi deployment

Before implementing a major feature:

1. Understand existing architecture.
2. Identify affected files.
3. Explain the implementation plan.
4. Implement only the requested feature.
5. Run tests.
6. Check for regressions.
7. Summarize changes.

If requirements are ambiguous, ask before making a major architectural decision.
