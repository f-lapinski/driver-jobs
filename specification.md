# PROJECT SPECIFICATION — Job Board Platform for Drivers and Employers

## Project Goal

To build an intuitive job board platform connecting employers and job seekers, with a focus on the transport industry and relevant qualifications (driver licenses, ADR, HDS). A web application with a modern frontend based on TailwindCSS, backend using Symfony 7, database PostgreSQL.

## User Types

- **Employer** (`ROLE_EMPLOYER`): posts job offers, browses candidates.
- **Job Seeker** (`ROLE_JOB_SEEKER`): submits CV/offers, browses job listings.
- **Moderator** (`ROLE_MODERATOR`): moderates content and accounts.
- **Administrator** (`ROLE_ADMIN`): manages users, roles, and global settings.

## Main Features

- Registration and login with role selection.
- Full user profile management (contact info, qualifications, experience, CV/logo).
- Creating, editing, removing job ads for both employers and job seekers.
- Search and filtering of offers by qualifications, location, driver license categories.
- Matching engine that suggests relevant ads from the opposite group.
- Admin and moderator control panels.
- Reporting system for inappropriate content.

## Data Models

### User
- id
- email
- password (hashed)
- roles (array)
- created_at

### EmployerProfile (1:1 relation with User)
- id
- user_id
- company_name
- tax_id (NIP)
- address
- description
- logo_url (optional)

### JobSeekerProfile (1:1 relation with User)
- id
- user_id
- first_name
- last_name
- experience
- licenses[] (many-to-many with LicenseCategory)
- additional_qualifications[] (many-to-many with AdditionalQualification)
- cv_url
- skills (text)

### LicenseCategory
- id
- name (e.g., "B", "C", "C+E", "D")

### AdditionalQualification
- id
- name (e.g., "ADR", "HDS")

### Ad (job advertisement)
- id
- user_id (author)
- title
- description
- licenses_required[] (many-to-many)
- qualifications_required[] (many-to-many)
- location
- salary
- contact
- created_at
- type (enum: employer/job_seeker)

## Technology Stack

- Symfony 7 + PHP 8
- Docker (optional)
- PostgreSQL
- Twig templating engine
- TailwindCSS for styling

## Functional Requirements

- User registration and login supporting at least two distinct roles from the start.
- Profile editing for employers and job seekers.
- Full CRUD (Create, Read, Update, Delete) for job advertisements.
- Filtering and searching ads by qualifications and license categories.
- Administration and moderation interfaces.
- Responsive and accessible user interface.

## Author

https://github.com/f-lapinski


