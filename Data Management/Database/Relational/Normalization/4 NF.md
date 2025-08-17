
Goal: Eliminate redundancy from independent multi-valued dependencies (Phones and DietaryRestrictions) by separating them; remove Cartesian product table AttendeeContactDiet.

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

### AttendeePrefTriple

| AttendeeID | Language | Tool   | Platform |
|------------|----------|--------|----------|
| A101       | Python   | Docker | Linux    |
| A101       | Python   | Docker | Windows  |
| A101       | Go       | Docker | Linux    |