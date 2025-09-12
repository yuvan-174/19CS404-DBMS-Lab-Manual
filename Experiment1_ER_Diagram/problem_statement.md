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
<img width="967" height="604" alt="image" src="https://github.com/user-attachments/assets/943b7cdf-47a3-4011-a505-726c0db69303" />


### Entities and Attributes

| **Entity**         | **Attributes (PK, FK)**                                          | **Notes**                                                                                        |
| ------------------ | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| **Member**         | PK: MemberID, Name, ContactInfo                                  | Members who borrow books or attend events.                                                       |
| **Book**           | PK: BookID, Title, Author, Category                              | Each book in the library collection.                                                             |
| **Loan**           | PK: LoanID, FK: MemberID, FK: BookID, LoanDate, ReturnDate, Fine | Tracks borrowing and overdue fines. Acts as associative entity for M\:N between Member and Book. |
| **Event**          | PK: EventID, EventName, Date, FK: RoomID                         | Library-organized cultural events.                                                               |
| **Room**           | PK: RoomID, RoomName, Capacity                                   | Rooms used for events and study.                                                                 |
| **Speaker**        | PK: SpeakerID, Name, Expertise                                   | Authors or speakers invited for events.                                                          |
| **Event\_Speaker** | FK: EventID, FK: SpeakerID                                       | Associative entity for M\:N between Event and Speaker.                                           |
| **Member\_Event**  | FK: MemberID, FK: EventID                                        | Associative entity for M\:N between Member and Event (registration).                             |


### Relationships and Constraints

| **Relationship**                     | **Cardinality**         | **Participation**                     | **Notes**                                                                           |
| ------------------------------------ | ----------------------- | ------------------------------------- | ----------------------------------------------------------------------------------- |
| Member – Loan – Book                 | M\:N (via Loan)         | Total on Loan, Partial on Member/Book | A member can borrow many books, a book can be borrowed by many members (over time). |
| Member – Event (via Member\_Event)   | M\:N                    | Partial participation (optional)      | Members may register for multiple events, and each event may have multiple members. |
| Event – Room                         | M:1                     | Total participation on Event          | Each event must occur in exactly one room, but a room can host many events.         |
| Event – Speaker (via Event\_Speaker) | M\:N                    | Partial participation                 | An event can have multiple speakers; a speaker can be invited to multiple events.   |
| Loan – Fine                          | 1:1 (attribute of Loan) | Optional participation                | Fine applies only if book is returned late.                                         |


### Assumptions
- Unique Identifiers: Every entity (Member, Book, Loan, Event, Room, Speaker) has a unique ID (MemberID, BookID, etc.) as the primary key.
- Membership Rules: Only registered members can borrow books or register for events.
- Book Lending Policy: A book can be borrowed by only one member at a time.
- Event Management: Each event is assigned to exactly one room.
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


### Entities and Attributes

| **Entity**      | **Attributes (PK, FK)**                                                             | **Notes**                                          |
| --------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------- |
| **Customer**    | PK: CustomerID, Name, Phone, Email                                                  | Customers who reserve or walk in                   |
| **Reservation** | PK: ReservationID, Date, Time, NumGuests, FK: CustomerID, FK: TableID, FK: WaiterID | Stores table bookings                              |
| **Table**       | PK: TableID, TableNumber, Capacity                                                  | Tracks tables in the restaurant                    |
| **Waiter**      | PK: WaiterID, WaiterName, Contact                                                   | Waiters assigned to reservations                   |
| **Order**       | PK: OrderID, OrderDateTime, FK: ReservationID                                       | Orders linked to reservations                      |
| **Dish**        | PK: DishID, DishName, Price, FK: CategoryID                                         | Food items on the menu                             |
| **Category**    | PK: CategoryID, CategoryName                                                        | Categories of dishes (starter, main, dessert)      |
| **Order\_Dish** | FK: OrderID, FK: DishID, Quantity                                                   | Associative entity for M\:N between Order and Dish |
| **Bill**        | PK: BillID, TotalAmount, ServiceCharge, FK: ReservationID                           | Bills generated per reservation                    |


### Relationships and Constraints

| **Relationship**               | **Cardinality** | **Participation**             | **Notes**                                                              |
| ------------------------------ | --------------- | ----------------------------- | ---------------------------------------------------------------------- |
| Customer – Reservation         | 1\:M            | Mandatory on Reservation side | One customer can make multiple reservations                            |
| Reservation – Table            | M:1             | Mandatory                     | Each reservation is assigned to one table                              |
| Reservation – Waiter           | M:1             | Mandatory                     | Each reservation is served by exactly one waiter                       |
| Reservation – Order            | 1\:M            | Optional                      | Some reservations may not result in orders (e.g., cancelled)           |
| Order – Dish (via Order\_Dish) | M\:N            | Mandatory                     | Each order has one or more dishes; each dish may appear in many orders |
| Dish – Category                | M:1             | Mandatory                     | Every dish belongs to exactly one category                             |
| Reservation – Bill             | 1:1             | Mandatory                     | Each reservation generates exactly one bill                            |


### Assumptions
- Unique Identifiers: Each entity has a unique primary key (CustomerID, ReservationID, TableID, etc.).
- Reservation Rules: A customer can book multiple reservations, but each reservation is for one table only.
- Waiter Assignment: Each reservation is served by exactly one waiter.
- Orders and Dishes: Orders are always linked to a reservation (no free-floating orders).
- Billing Policy: One bill is generated per reservation, covering all orders linked to it.
---


