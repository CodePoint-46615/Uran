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
