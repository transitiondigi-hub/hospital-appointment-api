# Hospital Appointment API — Test Cases

## TC-01: Book an Available Appointment

**Related Requirement:** FR-02

**Preconditions:**
- The patient exists in the system.
- The requested appointment slot is available.

**Test Steps:**
1. Send a valid appointment booking request.
2. Check the API response.

**Expected Result:**
- The booking is successful.
- A confirmation is returned.
- The appointment slot becomes unavailable for another booking.

## TC-02: Prevent Double Booking

**Related Requirements:** FR-03, BRULE-01

**Preconditions:**
- An appointment slot is already booked.

**Test Steps:**
1. Submit another booking request for the same slot.
2. Check the API response.

**Expected Result:**
- The second booking is rejected.
- The existing booking remains unchanged.
- The API returns the agreed conflict response.

## TC-03: Reject an Invalid Booking Request

**Related Requirement:** FR-02

**Preconditions:**
- The API is available.

**Test Steps:**
1. Submit a booking request with a required field missing.
2. Check the API response.

**Expected Result:**
- The booking is rejected.
- A validation error is returned.
- No appointment is created.
