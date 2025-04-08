# 10-cloud-functions-and-forms.md — Cloud Functions for Form Submissions

## Feature Title: Firebase Functions for Secure Contact Form Handling

## Objective
Implement a secure, scalable backend to receive and store contact form submissions:
- Submit data from Flutter Web → Python Cloud Function
- Validate and sanitize inputs
- Store in Firestore (in dev: emulator)
- Optionally send email or webhook

---

## Files to Modify / Create

| File | Purpose |
|------|---------|
| `functions/python/main.py` | Define `submit_contact_form` endpoint |
| `functions/python/validation.py` | Input validation rules |
| `functions/python/firestore.py` | Encapsulate DB access |
| `functions/python/test/test_main.py` | PyTest for function handler |

---

## API Endpoint

**POST** `/contact/submit`
```json
{
  "name": "Jane Doe",
  "email": "jane@company.com",
  "message": "Let's talk!"
}
```

**Success Response:** `200 OK` with `{ status: "ok" }`

**Failure:**
- `400 Bad Request` — missing or invalid fields
- `500 Internal Error` — unexpected exception

---

## Security Requirements
- Validate email format
- Sanitize input to prevent Firestore injection or abuse
- Rate limit by IP (future task)
- Use CORS header config in Flask

---

## Agent Instructions

### Pre-Implementation
- [ ] Confirm `7-contact-and-calendly.md` form is complete
- [ ] Load test cases from `post-task.md`
- [ ] Emulator must be running if not deploying live

### Implementation
- Use Flask route: `@app.route('/contact/submit', methods=['POST'])`
- Use Firebase Admin SDK to write to Firestore collection `contact_submissions`
- Log request IDs for traceability

### Post-Implementation
- [ ] Add PyTest with positive, negative, and malformed payloads
- [ ] Verify Firebase Emulator can accept writes locally
- [ ] Update `component-registry.md` with API function metadata
- [ ] Complete full `post-task.md` cycle

---

## Acceptance Criteria

As a **backend agent**, I can:
- ✅ Receive and validate contact form data from frontend
- ✅ Store submissions safely in Firestore
- ✅ Return correct success and error responses
- ✅ Write tests that simulate real input + errors
- ✅ Run 100% locally using Firebase Emulator

---

## Notes
This enables lead capture + CRM funnel entry.  
It must be **secure**, **clean**, and **easily extensible** (email/webhook next).

> 🛡️ The first line of backend defense — get it right.

