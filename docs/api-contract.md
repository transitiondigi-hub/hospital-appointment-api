# Hospital Appointment API — API Contract

## 1. Purpose

This document defines the API contract for creating a hospital appointment.

## 2. Endpoint

- **HTTP Method:** POST
- **Endpoint:** `/api/appointments`
- **Purpose:** Create a new appointment.
- **Content-Type:** `application/json`

## 3. Request Body

The client must send the following fields:

| Field | Data Type | Required | Description |
|---|---|---|---|
| `patientId` | Integer | Yes | Unique identifier of the patient |
| `doctorId` | Integer | Yes | Unique identifier of the doctor |
| `appointmentDate` | String (YYYY-MM-DD) | Yes | Requested appointment date |
| `appointmentTime` | String (HH:mm) | Yes | Requested appointment time |

### Example Request

```json
{
  "patientId": 125,
  "doctorId": 42,
  "appointmentDate": "2026-10-20",
  "appointmentTime": "10:30"
}
```

## 4. Success Response

**HTTP Status:** `201 Created`

```json
{
  "appointmentId": 9001,
  "status": "CONFIRMED"
}
```

## 5. Error Responses

### 400 Bad Request

**Scenario:** A required field is missing or contains invalid data.

Example response:

```json
{
  "errorCode": "INVALID_REQUEST",
  "message": "The request contains missing or invalid fields."
}
```

### 409 Conflict

**Scenario:** The requested appointment slot is already booked.

Example response:

```json
{
  "errorCode": "APPOINTMENT_SLOT_UNAVAILABLE",
  "message": "The selected appointment slot is not available."
}
```

### Error Response Rules

- The HTTP status code must match the error scenario.
- The response must contain an `errorCode`.
- The response must contain a human-readable `message`.
- The API must not create a confirmed appointment when the request is rejected.

## 6. Business Rules

- A time slot cannot have two confirmed appointments.
- An appointment can be confirmed only if the requested slot is available.

## 7. Open Questions

- Is authentication required?
- Can patients cancel or reschedule appointments?
- What validation rules apply to appointment dates and times?
- What is the agreed error response structure for invalid requests?
