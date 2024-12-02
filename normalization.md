### Normalization to Third Normal Form (3NF)

### Overview of Normalization
Normalization is a database design technique that reduces redundancy and dependency by organizing fields and table relationships. The primary goal is to isolate data so that additions, deletions, and modifications can be made without affecting other data.

## Normal Forms

# First Normal Form (1NF):
All attributes must contain atomic values.
Each record must be unique.

## Second Normal Form (2NF):
Must be in 1NF.
All non-key attributes must be fully functionally dependent on the primary key.

# Third Normal Form (3NF):
Must be in 2NF.
No transitive dependency; non-key attributes must not depend on other non-key attributes.

## Review of the Current Schema
# Entities and Attributes
- User
- Property
- Booking
- Payment
- Review
- Message

## Potential Redundancies and Violations
# User Entity:
No redundancy or violation. All attributes are relevant to the user.

# Property Entity:
The host_id is correctly referencing the User entity, maintaining 1NF and 2NF.

# Booking Entity:
The user_id and property_id are correctly used as foreign keys. Attributes are dependent on the composite key (booking_id), satisfying 1NF and 2NF.

# Payment Entity:
The amount and payment_method are directly related to booking_id, complying with 1NF and 2NF.

# Review Entity:
The rating and comment depend on both the property_id and user_id, and there's no transitive dependency, so it’s in 3NF.

# Message Entity:
The attributes are directly related to the message, satisfying 1NF, 2NF, and 3NF.


## Normalization Steps
# Ensure 1NF:
All tables have atomic values and unique records. No changes needed.

# Ensure 2NF:
All non-key attributes fully depend on the primary key. No changes needed.

# Ensure 3NF:
Check for transitive dependencies. In our schema, no non-key attribute depends on another non-key attribute. Thus, all entities are in 3NF.

# Final Schema in 3NF
The final schema remains the same as there were no violations or redundancies detected:

# User
* user_id (PK)
* first_name
* last_name
* email
* password_hash
* phone_number
* role
* created_at

# Property
* property_id (PK)
* host_id (FK -> User.user_id)
* name
* description
* location
* pricepernight
* created_at
* updated_at

# Booking
* booking_id (PK)
* property_id (FK -> Property.property_id)
* ser_id (FK -> User.user_id)
* start_date
* end_date
* total_price
* status
* created_at

# Payment
* payment_id (PK)
* booking_id (FK -> Booking.booking_id)
* amount
* payment_date
* payment_method

# Review
* review_id (PK)
* property_id (FK -> Property.property_id)
* user_id (FK -> User.user_id)
* rating
* comment
* created_at

# Message
* message_id (PK)
* sender_id (FK -> User.user_id)
* recipient_id (FK -> User.user_id)
* message_body
* sent_at


# Conclusion
* The database schema is in Third Normal Form (3NF) as it meets all the requirements of normalization without redundancies or transitive dependencies. This structure ensures data integrity and minimizes the risk of anomalies during data operations.