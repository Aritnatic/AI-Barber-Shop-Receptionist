# AI-Powered Voice Receptionist for Barber Shop Appointment Booking

A minor project submitted for the 4th Semester Diploma in Computer Science & Engineering  
**C.V. Raman Polytechnic, Bhubaneswar**

---

## About the Project

This project is an AI-powered voice receptionist that automates appointment booking for a barber shop. A customer calls and speaks to **Riley**, an AI voice assistant, who handles the entire booking process — checking availability, collecting details, confirming the appointment, and sending notifications — without any human involvement from the shop side.

---

## How It Works

The system has two automated paths:

- **Path 1 – Check Availability:** Riley asks for service, date, and time. The system queries a Google Sheet to find free slots and tells the customer what's available.
- **Path 2 – Finalize Booking:** Once the customer confirms a slot and provides their name and phone number, the booking is saved to the Google Sheet and notifications are sent via Telegram.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Vapi.ai | AI voice assistant platform (hosts Riley) |
| n8n | Workflow automation backend (handles all logic) |
| Google Sheets | Real-time booking database |
| Telegram Bot API | Notifications to owner and customer |
| ngrok | Exposes local n8n server to the internet |


## LOGIC BLUEPRINT

<img width="817" height="597" alt="image" src="https://github.com/user-attachments/assets/95cf2fbe-3121-4beb-8dba-2b983fe310a9" />

---

## Project Files

```
├── AI Rep for Barber Shop (COMPLETE).json   → n8n workflow (import this into n8n)
├── Minor_Project_Report_AI_Barber_Shop.docx → Full project report
├── USER_GUIDE.pdf                           → Step-by-step setup guide
└── README.md                                → This file
```

---

## Setup Instructions

> Follow the USER_GUIDE.pdf for detailed screenshots and steps. This is a quick summary.

**Prerequisites**
- n8n installed and running
- ngrok installed and authenticated (`ngrok config add-authtoken <your_token>`)
- A Google account with access to the shared Google Sheet
- A Vapi.ai account
- An Android phone with the SMS Gateway app (optional, for SMS)
- <img width="251" height="493" alt="image" src="https://github.com/user-attachments/assets/364d7ff6-e0fe-443f-92e5-cc7ff8c74f83" />


**Steps**

1. Open n8n → click the three dots (⋮) → Import from file → select the JSON file
2. Open the `Sheet: Lookup Existing Appointments` node → create a new Google OAuth2 credential using your Client ID and Client Secret
3. Verify the Spreadsheet URL and sheet tab name (`Bookings`) are correct
4. Repeat credential setup for the `Sheet: Add Confirmed Booking` node
5. Go to workflow Settings → change Timezone to `Asia/Kolkata`
6. Start ngrok and copy your public URL
7. In Vapi dashboard, update both tool server URLs with your ngrok link:
   - `checkAvailability` → `https://your-name.ngrok-free.app/webhook/check-availability`
   - `finalizeBooking` → `https://your-name.ngrok-free.app/webhook/sierra-booking-success`
8. Publish the assistant in Vapi and test using the Talk button

---

## Important Notice

This repository does **not** contain any private credentials.  
Before running the workflow, you must fill in your own:
- Google OAuth2 Client ID and Client Secret
- ngrok authtoken
- Telegram Bot Token and Chat ID

---

## Team

| Name | Registration No |
|------|----------------|
| Aritra Jana | F24029007017 |
| Seikh Imaad Aktar | F24029007086 |
| Tushar Kanta Panda | F24029007107 |
| Sagar Mandal | F24029007080 |
| Maaz Manzar | F24029007045 |

**Guide:** Ipsita Ankita Hota , C.V. Raman Polytechnic  
**Academic Year:** 2026
