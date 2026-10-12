# Hospital Appointment API — Requirements

## 1. Purpose
The system allows patients to book medical appointments through an API.

## 2. Business Requirements

**BR-01:** Patients should be able to book an available appointment.

**BR-02:** The system should prevent double booking of the same appointment slot.

## 3. Functional Requirements

**FR-01:** The system shall allow a patient to view available appointment slots.

**FR-02:** The system shall allow a patient to book an available appointment.

**FR-03:** The system shall reject a booking if the requested slot is already booked.

**FR-04:** The system shall return a booking confirmation after a successful booking.

## 4. Non-Functional Requirements

**NFR-01:** The API shall use HTTPS in production.

**NFR-02:** The API shall return a response within 2 seconds under the agreed normal operating load.

## 5. Business Rules

**BRULE-01:** A time slot cannot have two confirmed appointments.

**BRULE-02:** A booking can only be confirmed for an available slot.

## 6. Acceptance Criteria

**AC-01:** Given an available appointment slot, when a patient submits a valid booking request, then the system confirms the booking.

**AC-02:** Given a slot that is already booked, when another booking request is submitted for the same slot, then the system rejects the request.

## 7. Open Questions

- Is patient authentication required?
- Can a patient cancel or reschedule an appointment?
- Which HTTP status codes will be used for booking conflicts?
