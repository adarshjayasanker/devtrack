# DevTrack Domain Model

## Overview

DevTrack is a developer-focused project management system designed to organize engineering work through projects and tasks.
The Domain Model defines the core entities and their relationships within the system.

---

## Core Entities

### User

Represents a developer using the platform

Attributes: 
- id
- name
- email
- passwordHash
- createdAt

Capabilities
- create projects
- create tasks
- be assigned tasks

---

### Project

Represents a container for organizing related development work.

Attributes:
- id
- name
- description
- ownerId
- createdAt

Relationships:
- belongs to a User
- contain tasks

---

### Task

Represents a unit of work inside a project

Attributes
- id
- title
- description
- status (todo | in-progress | done)
- priority (low | medium | high)
- projectId
- assignedTo
- createdAt

---

## Relationships

User -> Projects
Project -> Tasks
User -> Assigned tasks

---

## Design Notes

The system introduces Projects as a boundary layer between Users and Tasks
This structure allows tasks to be grouped by context and prevents task lists from becoming unmanageable as the system scales.
