# ✈️ Air Ticket Booking & Boarding Management System

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Database](https://img.shields.io/badge/Database-Oracle-blue)
![Project-Type](https://img.shields.io/badge/Type-Academic%20DBMS%20Project-orange)
![License](https://img.shields.io/badge/License-AIUB--CSE-lightgrey)

## 🏫 Academic Information
**Institution:** American International University–Bangladesh (AIUB)  
**Department:** Computer Science & Engineering  
**Course:** Introduction to Database  
**Semester:** Spring 2022–2023  
**Section:** M  
**Group:** 01  
**Supervisor:** KAWSER IROM RUSHEE  
**Date of Submission:** May 17, 2023  

---

## 👥 Contributors
| Name | Student ID | Contribution |
|------|-------------|--------------|
| **Nafiur Rahman Niloy** | 22-46459-1 | Member |
| **Azminur Rahman** | 22-46588-1 | Member |
| **Saikot Kundu** | 22-46615-1 | Member |
| **Md. Sakib Sarwar** | 22-46625-1 | Member |

---

## 📘 Project Overview
**Project Title:** Air Ticket Booking & Boarding Management System  
**System Name:** *Uran*  

The **Air Ticket Booking & Boarding Management System** is designed for managing the operations of a fictional airline company called **“Uran”**.  
It handles booking, ticketing, passenger management, flight routes, and seat allocation within a normalized relational database structure.

---

## 🧩 Scenario Summary
- The company is managed by **Managers** who supervise **Ticket Agents**.  
- **Agents** sell tickets to **Customers**.  
- **Customers** can purchase tickets for themselves or for other **Passengers**.  
- **Passengers** require valid tickets for boarding planes.  
- The system maintains detailed information about **planes**, **routes**, **seats**, **payments**, and **addresses**.

Each entity (manager, agent, customer, passenger, plane, etc.) has unique identifiers and is linked using **foreign key relationships** to ensure data integrity.

---

## 🗃️ Database Design

### 🔹 ER Diagram
The database design includes an ER diagram representing all entities and their relationships:
- Manager → Agent  
- Agent → Ticket  
- Ticket → Customer → Passenger → Plane → Route → Seat  

*(Refer to the PDF for the full ER diagram screenshots and final schema.)*

---

## ⚙️ Normalization
All relations were normalized up to **Third Normal Form (3NF)** to eliminate redundancy and maintain consistency.  
Key tables normalized include:
- **Manages**
- **Sell**
- **Purchase**
- **Buy As/For**
- **Boarding**
- **Sits On**
- **Has**
- **Travels In**

Each step from **UNF → 1NF → 2NF → 3NF** is documented in the report with functional dependencies and table splits.

---

## 🧱 Final Tables
Final list of database tables after normalization and optimization:

1. `manager`  
2. `manager_contact`  
3. `agent`  
4. `agent_contact`  
5. `address`  
6. `customer`  
7. `customer_contact`  
8. `ticket`  
9. `payment`  
10. `plane`  
11. `passenger`  
12. `passenger_contact`  
13. `seat`  
14. `route`

---

## 🧾 SQL Implementation

### 📄 Table Creation
All tables were created using **Oracle SQL** syntax. Example:

```sql
CREATE TABLE manager (
  mgr_id NUMBER(3) CONSTRAINT pk_manager PRIMARY KEY,
  mgr_name VARCHAR2(30) NOT NULL,
  mgr_sal FLOAT NOT NULL CONSTRAINT manager_sal CHECK (mgr_sal BETWEEN 50000 AND 100000)
);
<<<<<<< HEAD
```

The schema includes:
- **Primary keys**
- **Foreign keys**
- **Check constraints**
- **Data integrity constraints**

---

## 🧍 Sample Data Insertion
Data was inserted into each table to simulate a real-world airline scenario.

Example:
```sql
INSERT INTO manager (mgr_id, mgr_name, mgr_sal) VALUES (100, 'Kawser', 99999);
INSERT INTO agent (a_id, a_name, a_sal, mgr_id) VALUES (459, 'Niloy', 30000, 100);
INSERT INTO ticket (t_id, amount, fare, departure, destination, p_date, d_date, baggage, a_id, c_id)
VALUES (45698745, 1, 4699, 'DHK', 'JES', TO_DATE('08-05-2023', 'DD-MM-YYYY'), TO_DATE('15-05-2023', 'DD-MM-YYYY'), 20, 459, 22466251);
```

---

## 🔍 SQL Operations

### 🪢 Joining
**Equi Join:**
```sql
SELECT c.c_name, c.c_gender, p.p_name, p.p_gender
FROM customer c, passenger p
WHERE c.c_id = p.c_id AND c.c_gender = p.c_gender;
```

**Outer Join (Left & Right):**
Retrieves customers and tickets even if one side has no corresponding records.

**Self Join:**
Retrieves agents and their corresponding manager names (if managed by another agent).

---

### 🧮 Subqueries
- Find agent with highest salary  
- Retrieve customers who purchased tickets above average fare  
- Identify customers whose names end with “n” and booked high-value tickets  

---

### 👁️ Views
**Complex View:**
```sql
CREATE VIEW customer_ticket_view AS
SELECT c.c_id, c.c_name, t.t_id, t.amount, t.fare, t.departure, t.destination
FROM customer c, ticket t
WHERE c.c_id = t.c_id;
```

**Simple View:**
```sql
CREATE VIEW manager_salary_view AS
SELECT mgr_name, mgr_sal FROM manager;
```

---

### 🧱 Constraints
Constraint added to ensure **non-negative and non-null payment history**:
```sql
ALTER TABLE customer
ADD CONSTRAINT check_pay_history_positive
CHECK (pay_history >= 0 AND pay_history IS NOT NULL);
```

---

## 🗂️ Project Contents
| Section | Description |
|----------|--------------|
| **ER Diagram** | Entity-relationship design and relationships |
| **Normalization** | 3NF conversion with detailed steps |
| **Table Creation** | SQL schema definitions |
| **Data Insertion** | Realistic sample data |
| **Joining & Subqueries** | Query practice and relational operations |
| **Views & Constraints** | Derived data and rule enforcement |

---

## 🧰 Tools & Technologies
- **Database:** Oracle SQL  
- **Environment:** Oracle SQL Developer / SQL*Plus  
- **Platform:** Windows  
- **Language:** SQL  

---

## 🏁 Conclusion
The **Air Ticket Booking & Boarding Management System** provides a complete, normalized database solution for managing the booking, boarding, and routing processes of an airline.  
The project successfully demonstrates:
- Proper **database normalization**  
- **Entity relationships** and **referential integrity**  
- Use of **joins, subqueries, and views** for analytical purposes  

