
Goal: Single wide record with repeating groups, multi-valued and composite attributes all embedded (before any normalization).

### RawRecord

| RegistrationID | EventDate  | AttendeeID | AttendeeName | AttendeeEmail        | AttendeePhones                              | DietaryRestrictions        | Tickets                                                                                                                                                | Preferences (Language;Tool;Platform)                        |
|----------------|-----------|------------|--------------|----------------------|----------------------------------------------|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|
| R5001          | 2025-10-12 | A101       | John Rivera  | johnd@example.com    | 555-1000;555-1001                            | Vegan;Nut-Free             | (TT1,Workshop Pass,150.00,ZW1,West Wing,V01,Convention Center,Denver);(TT2,Expo Pass,50.00,ZW1,West Wing,V01,Convention Center,Denver)                 | (Python,Docker,Linux);(Python,Docker,Windows);(Go,Docker,Linux) |

(Phones, dietary restrictions, and composite ticket & preference details are all packed into single cells.)