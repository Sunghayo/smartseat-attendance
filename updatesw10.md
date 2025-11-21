# SmartSeat System


---

## 1. Added Multi-Day Reservation Support (No More Single-Day Limitation)

### Previous Issue
- The initial version had **no date concept**.
- All pages assumed **one fixed date** (effectively Monday only).
- Reservation was not connected to actual days of the week.

### Improvements
- Implemented a complete **Mon–Fri weekday reservation system**.
- The selected date is preserved across all pages:

- Firestore now stores:
- `date (YYYY-MM-DD)`
- `weekday ("Mon", "Tue", etc.)`

### Example (add your screenshot)

<img width="645" height="737" alt="스크린샷 2025-11-21 22 47 13" src="https://github.com/user-attachments/assets/8ae2ee2a-76a1-468e-a864-107675ac3235" />

---

## 2. Data Consistency: Standardized Seats, Dates, Buildings, and Room Names

### Issue
- Seat data was inconsistently stored as:
- `"A1, A2"` → string format
- `["A1", "A2"]` → array format
- Buildings and room names also inconsistent.

### Improvements
- All seats are **always stored as arrays**.
- Naming conventions for building/rooms **fully standardized**.
- Ensures accurate seat counting & stable Firestore structure.

---

## 3. Teacher–Student Attendance Check System  
### (Including Backup Code-Based Attendance When AI Fails)

### Purpose
If AI image-based attendance fails (e.g., camera issue), students can still check in manually via a teacher-generated code.

### Key Features
- Teacher can generate a **daily attendance code** for each room.
- Students must enter the **correct code + correct date + correct room**.
- This code system is temporary; later can be replaced with:
- QR code
- Bluetooth proximity
- NFC tap

### Result
A reliable fallback attendance system that works even when AI is unavailable.

<img width="1274" height="1104" alt="스크린샷 2025-11-21 22 51 22" src="https://github.com/user-attachments/assets/48afec5e-3283-4c98-b0f1-ece24dbd40bb" />

<img width="724" height="854" alt="스크린샷 2025-11-21 22 52 03" src="https://github.com/user-attachments/assets/b4f0c928-581e-4ee9-aa7a-54bc2c890f54" />

---

## 4. Real Data–Driven Occupancy & Room Statistics Dashboard  
### (Replaced All Random/Meaningless Prototype Graphs)

### Previous Issue
- All charts (occupancy, trends, statistics) were **random values**.
- Meaningless from a real system perspective.

### Improvements
- All stats now use **real-time Firestore data**:
- Actual reservations per date
- Actual attendance status
- Actual seat usage
- Weekly occupancy trend graph now reflects:
- Mon–Fri real reservation counts
- Real occupancy percentage calculation

### Result
Professional, accurate dashboard based on real data – not simulation.

<img width="666" height="968" alt="스크린샷 2025-11-21 22 52 28" src="https://github.com/user-attachments/assets/6a38ecdb-a7e7-4159-8b1a-93cf66cccd92" />


---

## 5. Admin Tools: Teacher Can Review & Modify Attendance

### New Capabilities
- Teacher sees the full list of students who booked the room.
- Manually change:
- On-time
- Late
- Absent
- Pending
- Changes update:
- Room statistics
- Donut chart
- Occupancy figures
  
<img width="2514" height="341" alt="스크린샷 2025-11-21 22 52 50" src="https://github.com/user-attachments/assets/4e3ba247-45da-4603-ab3c-1aecc339927e" />


---

## 6. System Architecture Cleanup & Standardization

### Improvements
- Unified naming for buildings, rooms, dates, and seat data
- Fixed inconsistencies in how pages pass date parameters
- Removed redundant or duplicate DB functions
- Ensured every page reads/writes using the same Firestore structure


<img width="2020" height="905" alt="스크린샷 2025-11-21 22 53 34" src="https://github.com/user-attachments/assets/ede92117-a5c3-400c-b148-0673346de615" />

---

## Summary

SmartSeat has evolved from a visual prototype into a fully data-driven reservation and attendance system, with reliable weekly scheduling, teacher controls, and real occupancy analytics.

