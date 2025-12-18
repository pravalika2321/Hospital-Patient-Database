Hospital Patient Management System (SQL)
📋 Project Overview
The Hospital Patient Database is a robust relational database solution designed to digitize healthcare workflows. It manages the interdependencies between patients, medical staff, scheduling, and financial transactions. This system ensures data integrity while providing administrative insights into hospital operations, doctor performance, and revenue cycles.

🚀 Key Features
Patient & Clinical Tracking: Maintains comprehensive records of patient demographics and medical history.

Appointment Lifecycle: Streamlines scheduling, allowing for real-time updates and cancellations to optimize doctor availability.

Financial Management: Tracks billing statuses (Paid, Pending, Cancelled) to ensure seamless revenue collection.

Performance Analytics: Generates reports on doctor productivity and departmental income.

🏗️ Database Schema
The database is built on a highly interconnected schema to ensure referential integrity:

Patients: Core demographic and medical history data.

Doctors: Professional details and specialization mapping.

Appointments: The bridge entity connecting Patients and Doctors with status tracking.

Billing: Financial records linked directly to patient visits.

🛠️ Technical Implementations
1. Relational Integrity
Used Foreign Keys and Cascading Actions to ensure that an appointment cannot exist without a valid patient and doctor, preventing "orphan" data records.

2. Advanced Analytical Queries
I developed specific queries to transform raw data into healthcare business intelligence:

Doctor Performance: Aggregating appointment counts and revenue generated per physician.

Financial Auditing: Identifying all "Pending" bills to assist the finance department in debt recovery.

Visit History: Using JOIN operations to retrieve a chronological medical timeline for specific patients.
