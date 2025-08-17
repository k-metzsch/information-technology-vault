
Goal: Eliminate non-trivial join dependencies by decomposing triple preferences into pairwise compatibility tables whose natural join reconstructs exactly the valid triples.

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

### Venues

| VenueID | VenueName          | VenueCity |
|---------|--------------------|-----------|
| V01     | Convention Center  | Denver    |

### Zones

| ZoneID | ZoneName  | VenueID |
|--------|-----------|---------|
| ZW1    | West Wing | V01     |

### TicketTypes

| TicketTypeID | TicketTypeName | BasePrice | ZoneID |
|--------------|----------------|-----------|--------|
| TT1          | Workshop Pass  | 150.00    | ZW1    |
| TT2          | Expo Pass      | 50.00     | ZW1    |

### Tickets

| RegistrationID | TicketTypeID |
|----------------|--------------|
| R5001          | TT1          |
| R5001          | TT2          |

### AttendeePhones

| AttendeeID | Phone     |
|------------|-----------|
| A101       | 555-1000  |
| A101       | 555-1001  |

### AttendeeDietaryRestrictions

| AttendeeID | DietaryRestriction |
|------------|--------------------|
| A101       | Vegan              |
| A101       | Nut-Free           |

### AttendeeLanguageTool

| AttendeeID | Language | Tool   |
|------------|----------|--------|
| A101       | Python   | Docker |
| A101       | Go       | Docker |

### AttendeeLanguagePlatform

| AttendeeID | Language | Platform |
|------------|----------|----------|
| A101       | Python   | Linux    |
| A101       | Python   | Windows  |
| A101       | Go       | Linux    |

### AttendeeToolPlatform

| AttendeeID | Tool   | Platform |
|------------|--------|----------|
| A101       | Docker | Linux    |
| A101       | Docker | Windows  |

### (Derived Valid Triples)

| AttendeeID | Language | Tool   | Platform |
|------------|----------|--------|----------|
| A101       | Python   | Docker | Linux    |
| A101       | Python   | Docker | Windows  |
| A101       | Go       | Docker | Linux    |