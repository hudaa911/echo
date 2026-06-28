# 🗃 Database Design

# Echo

## Overview

Echo uses MongoDB as its primary database.

The application stores users, ideas, journal entries, tags, and relationships between ideas.

The database is designed to support connected thinking rather than isolated note storage.

---

# Collections

## 1. Users

Stores account information.

### Fields

* _id
* name
* email
* password
* profileImage
* createdAt
* updatedAt

---

## 2. Ideas

Stores all captured ideas.

### Fields

* _id
* title
* description
* tags
* favorite
* userId
* createdAt
* updatedAt

Each idea belongs to one user.

---

## 3. Tags

Stores reusable tags.

### Fields

* _id
* name
* color
* userId

One tag can be attached to many ideas.

---

## 4. Connections

Stores relationships between ideas.

### Fields

* _id
* sourceIdeaId
* targetIdeaId
* relationshipType
* createdAt

Examples of relationshipType:

* Inspired By
* Leads To
* Related To
* Supports

---

## 5. Journal Entries

Stores daily reflections.

### Fields

* _id
* title
* content
* mood
* date
* userId
* createdAt

Each journal entry belongs to one user.

---

# Relationships

User
│
├── Ideas
├── Journal Entries
└── Tags

Idea
│
├── Tags
└── Connections

Connections
│
├── Source Idea
└── Target Idea

---

# Relationship Types

One User
→ Many Ideas

One User
→ Many Journal Entries

One User
→ Many Tags

One Idea
→ Many Connections

One Tag
→ Many Ideas

---

# MongoDB Collections

users

ideas

tags

connections

journalEntries

---

# Indexing Strategy

Indexes should be created on:

* email
* title
* tags
* createdAt

This improves search performance.

---

# Future Collections

notifications

attachments

voiceNotes

knowledgeGraphs

sharedWorkspaces

activityLogs

These collections are planned for future releases.
