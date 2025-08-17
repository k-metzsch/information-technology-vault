
Goal: Make attributes atomic; move repeating groups to separate tables (still leaving partial & transitive dependencies, and multi-valued Cartesian combos).

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

### Tickets  
(Still includes attributes only dependent on TicketTypeID → partial & transitive issues)

| RegistrationID | TicketTypeID | TicketTypeName | BasePrice | ZoneID | ZoneName   | VenueID | VenueName          | VenueCity |
|----------------|--------------|----------------|-----------|--------|------------|---------|--------------------|-----------|
| R5001          | TT1          | Workshop Pass  | 150.00    | ZW1    | West Wing  | V01     | Convention Center  | Denver    |
| R5001          | TT2          | Expo Pass      | 50.00     | ZW1    | West Wing  | V01     | Convention Center  | Denver    |

### AttendeeContactDiet  
(Cartesian of Phones × DietaryRestrictions)

| AttendeeID | Phone     | DietaryRestriction |
|------------|-----------|--------------------|
| A101       | 555-1000  | Vegan              |
| A101       | 555-1000  | Nut-Free           |
| A101       | 555-1001  | Vegan              |
| A101       | 555-1001  | Nut-Free           |

### AttendeePrefTriple  
(Preferences as triples)

| AttendeeID | Language | Tool   | Platform |
|------------|----------|--------|----------|
| A101       | Python   | Docker | Linux    |
| A101       | Python   | Docker | Windows  |
| A101       | Go       | Docker | Linux    |