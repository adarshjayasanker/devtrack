# DevTrack Domain Model

## Overview

DevTrack is a developer-focused project management system designed to organize engineering work through Projects and Tasks.

This document defines the core entities and relationships that structure the system.

---

## Core Entities

### User

Represents a developer using the platform.

Attributes

- id (ObjectId)
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

Attributes

- id (ObjectId)
- name
- description
- ownerId (User reference)
- createdAt

Relationships

- belongs to a User
- contains multiple Tasks

---

### Task

Represents a unit of work inside a Project.

Attributes

- id (ObjectId)
- title
- description
- status (todo | in-progress | done)
- priority (low | medium | high)
- projectId (Project reference)
- assignedTo (User reference)
- createdAt

---

## Relationships

User → Projects  
Project → Tasks  
User → Assigned Tasks

---

## Design Notes

Projects act as the organizational boundary between Users and Tasks.

Instead of allowing users to maintain a global task list, tasks are grouped within Projects. This structure improves scalability and keeps task management context-specific as the system grows.