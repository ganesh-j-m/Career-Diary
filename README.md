# 🌐 Career Katta - Digital Diary (करिअर कट्टा - डिजिटल डायरी)

An automated, secure, and highly restricted web application designed for students under the **Career Katta** initiative (supported by the Maharashtra Information Technology Support Centre - MITSC). This digital portal replaces the traditional paper diary, allowing students to efficiently log their monthly academic progress, track career goals, and receive digital certificates upon completion.

---

## 🚀 Key Features

### 🏢 1. Official & Responsive UI
* **Professional Layout:** Designed with official branding, featuring the Maharashtra Government logo and the MITSC emblem.
* **Responsive Design:** Fully responsive interface built using Bootstrap 5, optimized for mobile, tablet, and desktop viewports.

### 🔒 2. Profile Verification & Data Locking
* **WhatsApp Verification:** Simple access via a 10-digit WhatsApp number that automatically retrieves existing user records.
* **Strict Profile Locking:** To prevent data tampering, personal details (College Name, Principal, Coordinator, and Student Name) are permanently locked and disabled once submitted.
* **Goal Setting:** Dedicated fields for students to articulate their long-term career visions via **Plan A** and **Plan B**.

### ⚡ 3. Smart Controls & Validation (Security Logic)
* **Future Month Restriction:** Implements strict real-time validation based on the current system date. Students **cannot** view or fill data for future months (e.g., if it is August, September remains locked with an alert: `🔒 हा महिना अजून सुरू झालेला नाही!`).
* **Sequential Data Progression:** Enforces strict compliance where a student must successfully submit the current month before the system unlocks the next month's form.
* **Smart Auto-Navigation:** Upon logging in, the system automatically analyzes past submissions and redirects the user directly to their next pending month.

### 📊 4. Monthly Progress Dashboard
Captures data every month across 4 mandatory core fields:
1. 📚 **Book of the Month** (पुस्तकाचे नाव)
2. 🛠️ **Skill Acquired** (कौशल्य)
3. 🤝 **Special Meeting/Visit** (विशेष भेट)
4. 🌟 **Activity/Initiative** (उपक्रम)

### 🏆 5. Automated Digital Certification
* **Interim Certificate:** Automatically unlocked and made available for download upon successful completion of **December** (Phase 1).
* **Final Certificate:** Unlocked at the end of the cycle in **June** (Final Phase).
* **Real-time Generation:** Generates professional Landscape PDFs on-the-fly containing the student's name, current date, and an embedded digital signature using `jsPDF`.

---

## 🛠️ Technology Stack

* **Frontend:** HTML5, CSS3, Bootstrap 5
* **Database:** Firebase Realtime Database (structured under `DiaryUsers/{mobile_number}/` for ultra-fast queries)
* **Libraries:** jsPDF (Client-side PDF generation)
* **Typography:** Google Fonts (*Khand* for sharp Marathi text rendering and *Poppins* for clean English layouts)

---

## 🗄️ Database Architecture

The user data is cleanly decoupled in Firebase to optimize read/write speeds:
```json
DiaryUsers/
└── {Student_Mobile_Number}/
    ├── ProfileDetails/
    │   ├── studentName: "..."
    │   ├── collegeName: "..."
    │   ├── planA: "..."
    │   └── planB: "..."
    └── MonthlyProgress/
        ├── July/
        │   ├── book: "..."
        │   ├── skill: "..."
        │   └── status: "Completed"
        └── August/
            └── ...
