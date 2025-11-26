# Hospital Management Package (Oracle PL/SQL)
## 👥 Group Members
1. **Niyonshuti samuel** -28329
2. **Mutabazi darius** -28239
3. **Ishimwe alsene** -28429


## 1.Database Tables Creation
## Patients Table

![patients](https://github.com/dariusmutabazi-commits/files/blob/main/Table%20creation%20patients.png)
Stores patient information:
- `patient_id` (Primary Key, Identity)
- `name`
- `age`
- `gender`
- `admitted_status` (`YES`/`NO`)
  ### Doctors Table

![doctors](https://github.com/dariusmutabazi-commits/files/blob/main/Table%20creation%20doctor.png)

Stores doctor information:
- `doctor_id` (Primary Key, Identity)
- `name`
- `specialty`
---

# 2.Package Specification (hospital_pkg)
![doctors](https://github.com/dariusmutabazi-commits/files/blob/main/package%20specification%201.png)
![doctors](https://github.com/dariusmutabazi-commits/files/blob/main/package%20specification%202.png)
![doctors](https://github.com/dariusmutabazi-commits/files/blob/main/package%20specification%203.png)

# 3.Package Body Implementation
![doctors](https://github.com/dariusmutabazi-commits/files/blob/main/package%20body%201.png)
![doctors](https://github.com/dariusmutabazi-commits/files/blob/main/package%20body%202.png)


# Project Overview
This project implements a modular PL/SQL package designed for a hospital setting. It simplifies how patient and doctor information is processed by using bulk operations, structured types, and cursor-based data retrieval. The goal is to provide a clean, efficient backend for hospital data management.

 # Database Structure
## Patients Table
Manages records of patients with fields such as:
patient_id — auto-generated primary key
name — full name
age — integer value representing age
gender — male/female
admitted_status — whether the patient is admitted
Doctors Table
Stores information related to doctors:
doctor_id — auto-generated primary key
name — doctor’s name
specialty — medical specialization

## Package Functionality (hospital_pkg)
The package provides:
Custom collection type: patient_tab for handling multiple patients at once
Bulk loading procedure using FORALL
Data retrieval cursor returning all patient records
Function for counting admitted patients
Procedure for updating a patient’s admission status

# Testing & Usage Examples
## 1. Bulk Insert Patients
```sql
DECLARE
  l_patients hospital_pkg.patient_tab := hospital_pkg.patient_tab();
BEGIN
  l_patients.EXTEND(2);
  l_patients(1).name := 'diane';
  l_patients(1).age := 30;
  l_patients(1).gender := 'F';
  l_patients(1).admitted_status := 'NO';

  l_patients(2).name := 'dad';
  l_patients(2).age := 45;
  l_patients(2).gender := 'M';
  l_patients(2).admitted_status := 'NO';

  hospital_pkg.bulk_load_patients(l_patients);
END;
/
```
## 2. Retrieve All Patients
Uses a REF CURSOR to fetch all data.
## 3. Admit a Patient
```sql
EXEC hospital_pkg.admit_patient(1);
```
## 4. Count Currently Admitted Patients
```sql
SELECT hospital_pkg.count_admitted FROM dual;
```


# Conclusion
This PL/SQL package successfully demonstrates bulk operations, cursor-based retrieval, and record updates — all essential components in building a reliable hospital information management backend. The structure is clean, maintainable, and meets the project requirements.
# ishimwe-alsene-pl-sql-group-assignment-group-b
