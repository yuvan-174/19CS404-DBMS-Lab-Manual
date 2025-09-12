# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="581" height="701" alt="image" src="https://github.com/user-attachments/assets/518b5ea7-0883-4a7a-9dc0-169f1852578a" />

### Entities and Attributes

| Entity        | Attributes (PK, FK)                          |  Notes                                                                                                                       |
|---------------|--------------------------------------------- |------------------------------------------------------------------------------------------------------------------------------|
| ADMIN         |login_id (PK), login_username, user_password  |The primary key is login_id. This entity represents an administrator with login credentials.                                  |
| User          |User_id (PK), user_name                       |A generic user entity, likely for authentication and basic profile. User_id is the primary key.                               |
| Permission    |Per_id (PK), Per_Name, per_module             |Represents a specific permission or role within the system, e.g., 'read-only', 'editor', 'manager'. Per_id is the primary key.| 
| Member        |Member_id (PK), Member_name                   |Represents a member of the fitness club. Member_id is the primary key.                                                        | 
| Trainer       |Trainer_id (PK), Trainer_name                 |Represents a fitness trainer. Trainer_id is the primary key.                                                                  |
| Branch        |BR_id (PK), BR_Name, BR_add                   |Represents a physical branch or location of the fitness club. BR_id is the primary key.                                       | 
| Fitness       |fit_type (PK), FIT_desc                       |Represents a type of fitness activity (e.g., Yoga, Zumba). fit_type is the primary key.                                       |


### Relationships and Constraints

| Relationship               | Cardinality | Participation           | Notes |
|----------------------------|-------------|-------------------------|-------------------------------------------------------|
|   ADMIN - has - Permission |One-to-Many  |Mandatory for Permission |An ADMIN can have multiple Permissions, but each Permission is granted to only one ADMIN (implying a specific Admin's set of permissions).
|User - has - ADMIN          |One-to-One   |Optional for User        |A User can be an ADMIN, and an ADMIN is also a User. This suggests a specialization relationship where ADMIN is a sub-type of User. The diagram uses has, which is not ideal for specialization, but this is the likely intent.
|User - MANAGE - Branch      |Many-to-Many |Optional for both        |A User (likely a manager or admin) can manage multiple Branches, and a Branch can be managed by multiple Users. The diagram shows User and Branch linked via the Manage diamond.  
|Member - MANAGE - Branch    |One-to-Many  |Optional for Branch      |A Member is associated with one Branch. This implies a member belongs to a specific branch.  
|Trainer - MANAGE - Branch   |One-to-Many  |Optional for Branch      |A Trainer is associated with one Branch. This implies a trainer works at one branch. 
|Member - HAS - Fitness      |Many-to-Many |Not explicitly shown     |A Member can have multiple Fitness types, and each Fitness type can have multiple Members. The HAS diamond connects them, representing a multi-valued relationship.                      |

### Assumptions
- Role Specialization: The diagram implies a user hierarchy where Admin is a specialized type of User, but Member and Trainer are modeled as separate entities.

- Ambiguous Relationships: The "Manage" relationship is used broadly for multiple roles, making it unclear whether a User, Member, or Trainer's interaction with a Branch is for management, employment, or membership.

- Data Redundancy: The separation of User and Member entities with similar attributes (name, etc.) suggests potential data redundancy in the system.

- Implicit Cardinality: The relationships lack explicit cardinality notation, requiring assumptions about whether one Trainer works at one Branch or many, or if a Member can belong to multiple Branches.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
