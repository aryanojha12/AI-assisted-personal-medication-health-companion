# PulseScript

**AI-Powered Personal Health Monitor and Medication Companion**

PulseScript is a patient-first health platform designed to bring prescriptions, medical records, medication schedules, wellness data, and emergency support into a single, user-friendly experience.

---

## Overview

PulseScript consolidates fragmented personal health information into one organized system, giving patients clear visibility into their prescriptions, records, and medication schedules while keeping them in control of their data.

---

## Core Features

### Smart Prescription Digitization
Converts handwritten or printed prescriptions into structured, readable medication information using AI and OCR.

### Medication Management
Extracts medicine name, dosage, frequency, duration, and instructions, then creates reminders following patient confirmation.

### Personal Health Vault
Keeps medical reports, prescriptions, lab results, and other health documents organized in a single, secure location.

### AI Health Assistant
Helps users understand their medical information in plain language through retrieval-grounded responses.

### Health Monitoring
Designed to integrate steps, heart rate, sleep, hydration, and other wearable data.

### Emergency SOS
Captures the user's location, generates an Emergency Health Card, and notifies emergency contacts. Emergency dispatch is clearly labeled as simulated unless a real provider integration is connected.

### Doctor Sharing and Consent
Patients control who can access their health information, and for how long.

### Trust and Provenance
AI-extracted medical facts are clearly separated from original records and labeled as unverified, patient-confirmed, or doctor-confirmed.

---

## Problem Statement

Patients often have medical information scattered across hospitals, laboratories, prescriptions, messaging apps, paper files, and multiple healthcare providers. Handwritten prescriptions can be difficult to interpret, medication schedules are easy to forget, and critical health information may not be readily available during an emergency.

PulseScript aims to make personal healthcare information organized, understandable, accessible, and actionable, while keeping the patient in control of their data.

---

## Planned Architecture

```text
Next.js Web App
      |
      v
FastAPI Backend
      |
 -----+---------------
 |    |               |
 v    v               v
PostgreSQL        Supabase Storage
+ pgvector        Medical Documents
      |
      v
AI / OCR Pipeline
      |
 -----+---------------
 |    |               |
 v    v               v
Clinical Data     RAG Assistant
Extraction        & Explanations
```

The initial architecture uses a single FastAPI backend, PostgreSQL, Supabase Storage, and asynchronous background processing, keeping the system practical for a hackathon build while leaving room to scale later.

---

## Core Data Principles

PulseScript distinguishes between the following categories of information:

1. **Original medical records** — the uploaded source documents.
2. **AI-extracted information** — structured facts extracted from those documents.
3. **AI-generated explanations** — summaries and assistant responses.
4. **Patient-confirmed information** — facts reviewed by the patient.
5. **Doctor-confirmed information** — facts reviewed by a treating doctor.

AI must not silently modify original medical records, and uncertain extractions require human confirmation before being treated as fact.

---

## Privacy and Safety

- Patient data is private by default.
- Access is controlled through authentication, role-based permissions, and explicit consent.
- Document access and other important actions are audit logged.
- Original uploaded records are treated as immutable.
- Medication reminders are created only from confirmed medication information.
- The AI assistant is designed to explain health information, not replace a qualified doctor.
- Emergency functionality must never claim that a real ambulance was dispatched unless a real dispatch integration confirms it.

---

## Planned Technology Stack

**Frontend**
- Next.js
- React
- TypeScript
- Tailwind CSS
- shadcn/ui

**Backend**
- Python
- FastAPI
- SQLAlchemy
- Alembic
- Pydantic

**Database and Storage**
- PostgreSQL
- pgvector
- Supabase Auth
- Supabase Storage

**AI**
- Vision/OCR provider for prescription and document extraction
- LLM for structured extraction and health explanations
- Embeddings and RAG for document-grounded assistance

**Integrations**
- Firebase/Web Push for notifications
- Wearable APIs
- Maps/location services
- Emergency-service adapter (simulated for the hackathon unless a real API is connected)

---

## Development Status

**Current stage:** Prototype / Development

The system is being developed incrementally, beginning with authentication, patient profiles, the medical document vault, prescription digitization, medication management, AI assistance, and emergency support.

**Hackathon note:** External integrations that are not connected to real APIs must be clearly labeled as simulated. No simulated action should be presented as a real-world medical or emergency service.

---

## Future Scope

- Mobile application
- Apple Health / Google Health Connect integration
- Additional wearable device support
- Verified doctor and healthcare-provider network
- Real emergency-service integrations
- Multilingual prescription and health explanations
- Family and caregiver accounts
- Personalized wellness and nutrition insights
- Advanced health trends and longitudinal analysis
- Healthcare-provider and insurance ecosystem integrations

---

## Medical Disclaimer

PulseScript is a healthcare information and organization tool. AI-generated information may contain errors and is not a substitute for professional medical diagnosis, treatment, or emergency medical services. Patients should verify medication information and consult qualified healthcare professionals for medical decisions.

---

## License

License to be added before public release.
