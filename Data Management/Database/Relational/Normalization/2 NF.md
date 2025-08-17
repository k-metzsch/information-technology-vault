
Goal: Remove partial dependencies (non-key columns in Tickets depending only on TicketTypeID). Introduce TicketTypes; Tickets keeps only attributes fully dependent on (RegistrationID, TicketTypeID). Transitive dependencies (ZoneID → VenueID → VenueCity) remain.

### Registrations

| RegistrationID | EventDate  |
|----------------|------------|
| R5001          | 2025-10-12 |

### Attendees

| AttendeeID | AttendeeName | AttendeeEmail       |
|------------|--------------|---------------------|
| A101       | John Rivera  | johnd@example.com   |

### RegistrationAttendees

| RegistrationID | AttendeeID |
|----------------|------------|
| R5001          | A101       |

### TicketTypes  
(Still has transitive dependencies)

| TicketTypeID | TicketTypeName | BasePrice | ZoneID | ZoneName   | VenueID | VenueName          | VenueCity |
|--------------|----------------|-----------|--------|------------|---------|--------------------|-----------|
| TT1          | Workshop Pass  | 150.00    | ZW1    | West Wing  | V01     | Convention Center  | Denver    |
| TT2          | Expo Pass      | 50.00     | ZW1    | West Wing  | V01     | Convention Center  | Denver    |

### Tickets

| RegistrationID | TicketTypeID |
|----------------|--------------|
| R5001          | TT1          |
| R5001          | TT2          |

### AttendeeContactDiet

| AttendeeID | Phone     | DietaryRestriction |
|------------|-----------|--------------------|
| A101       | 555-1000  | Vegan              |
| A101       | 555-1000  | Nut-Free           |
| A101       | 555-1001  | Vegan              |
| A101       | 555-1001  | Nut-Free           |

### AttendeePrefTriple

| AttendeeID | Language | Tool   | Platform |
|------------|----------|--------|----------|
| A101       | Python   | Docker | Linux    |
| A101       | Python   | Docker | Windows  |
| A101       | Go       | Docker | Linux    |