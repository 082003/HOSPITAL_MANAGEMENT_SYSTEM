# Hospital Management System 🏥

A robust, console-based **Hospital Management System** application built using **Core Java (JDBC)** and **PostgreSQL** database. This project manages critical hospital workflows such as registering patients, viewing professional doctor profiles, and real-time appointment booking with automatic slot availability validation.

---

## 🚀 Key Features

- **Patient Management:** Add new patient details (Name, Age, Gender) securely and display full patient records in structured ASCII tables.
- **Doctor Management:** View active doctor records, including specialized fields and unique IDs.
- **Smart Appointment Booking:** Checks real-time availability of doctors for a specific date before booking. Prevents duplicate slots or double-bookings seamlessly using custom database checks.
- **Robust Exception Handling:** Integrated safe database boundaries using SQL error containment strategies to log errors gracefully without application crashes.

---

## 🛠️ Tech Stack & Prerequisites

- **Language:** Java (JDK 8 or higher)
- **Database:** PostgreSQL (v14 or higher recommended)
- **Database GUI:** pgAdmin
- **Driver:** PostgreSQL JDBC Driver (`org.postgresql.Driver`)
- **IDE:** JetBrains IntelliJ IDEA

---

## 📦 Database Setup (PostgreSQL)

Run the following SQL schemas in your pgAdmin Query Tool to create the required relational structures:

```sql
-- 1. Create Patients Table
CREATE TABLE patients (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    gender VARCHAR(10) NOT NULL
);

-- 2. Create Doctors Table
CREATE TABLE doctors (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    specialization VARCHAR(100) NOT NULL
);

-- 3. Create Appointments Table
CREATE TABLE appointments (
    id SERIAL PRIMARY KEY,
    patient_id INT REFERENCES patients(id),
    doctor_id INT REFERENCES doctors(id),
    appointment_date DATE NOT NULL
);

-- Optional: Insert dummy doctors for immediate use
INSERT INTO doctors (name, specialization) VALUES 
('Dr. Ramesh Sharma', 'Cardiologist'),
('Dr. Priya Patel', 'Dermatologist'),
('Dr. Amit Verma', 'Pediatrician');


