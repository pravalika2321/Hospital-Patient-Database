## 🏥 Hospital Patient Database System

### Project Overview

The Hospital Patient Database is a relational database system designed to centralize healthcare data. It ensures that patient records, doctor schedules, and financial transactions are linked seamlessly, reducing administrative overhead and improving patient care.

---

### 1. Database Schema Design

The system is built around four primary entities. The relationships ensure data integrity (e.g., you cannot have a bill without a patient).

| Table | Key Responsibility | Primary Key | Foreign Keys |
| --- | --- | --- | --- |
| **Patients** | Stores personal and contact information. | `PatientID` | None |
| **Doctors** | Stores specialization and contact info. | `DoctorID` | None |
| **Appointments** | Links patients to doctors with time/status. | `ApptID` | `PatientID`, `DoctorID` |
| **Billing** | Tracks costs, payment status, and dates. | `BillID` | `PatientID`, `ApptID` |

---

### 2. Implementation Steps

#### Step 1: Table Creation (SQL)

To maintain data integrity, we use **Foreign Keys** with `ON DELETE CASCADE` or `SET NULL` actions.

```sql
-- Example: Creating the Appointments Table
CREATE TABLE Appointments (
    ApptID INT PRIMARY KEY AUTO_INCREMENT,
    PatientID INT,
    DoctorID INT,
    AppointmentDate DATETIME,
    Status ENUM('Scheduled', 'Completed', 'Cancelled'),
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID),
    FOREIGN KEY (DoctorID) REFERENCES Doctors(DoctorID)
);

```

#### Step 2: Core Functionalities

The system supports the following CRUD (Create, Read, Update, Delete) operations:

* **Registration:** Enrollment of new patients and onboarding of medical staff.
* **Scheduling:** A dynamic appointment system where status updates (e.g., from "Scheduled" to "Completed") trigger medical history logs.
* **Financials:** Automated billing generation upon appointment completion with status tracking (**Paid, Pending, Cancelled**).

---

### 3. Advanced Features & Analytics

Beyond basic storage, the database is optimized for reporting:

* **Medical History Tracking:** A view or join query that compiles all past appointments and diagnoses for a specific `PatientID`.
* **Revenue Reports:** Total Revenue = \sum (Amount) where Status = 'Paid'
* **Doctor Performance:** Monthly reports calculating the total number of patients seen and the revenue generated per doctor.

---

### 4. Sample Testing Queries

To verify the system, use the following logic:

**A. Find all pending bills for a specific patient:**

```sql
SELECT * FROM Billing WHERE Status = 'Pending' AND PatientID = 101;

```

**B. Check Doctor Availability:**

```sql
SELECT AppointmentDate FROM Appointments 
WHERE DoctorID = 5 AND Status = 'Scheduled';

```

---

### 5. Installation & Setup

1. **Environment:** Ensure you have a SQL environment (MySQL, PostgreSQL, or SQL Server) installed.
2. **Schema Execution:** Run the `schema.sql` script to create tables.
3. **Data Seeding:** Run `seed_data.sql` to populate the database with test records.
4. **Verification:** Execute the testing queries provided in the `tests/` folder.

> **Note:** For production environments, ensure **HIPAA compliance** (or local data protection laws) by implementing encryption for the `Patients` table and restricted access roles for `Billing` data.

---

