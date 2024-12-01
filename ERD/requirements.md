An Entity-Relationship (ER) diagram, I'll outline the entities, their attributes, and the relationships between them. Here's how it will be structured:

### Entities and Attributes

## User

1. user_id (PK)
2. first_name
3. last_name
4. email
5. password_hash
6. phone_number
7. role
8. created_at

## Property
1. property_id (PK)
2. host_id (FK -> User.user_id)
3. name
4. description
5. location
6. pricepernight
7. created_at
8. updated_at

## Booking
1. booking_id (PK)
2. property_id (FK -> Property.property_id)
3. user_id (FK -> User.user_id)
4. start_date
5. end_date
6. total_price
7. status
8. created_at

## Payment
1. payment_id (PK)
2. booking_id (FK -> Booking.booking_id)
3. amount
4. payment_date
5. payment_method

## Review
1. review_id (PK)
2. property_id (FK -> Property.property_id)
3. user_id (FK -> User.user_id)
4. rating
5. comment
6. created_at

## Message
1. message_id (PK)
2. sender_id (FK -> User.user_id)
3. recipient_id (FK -> User.user_id)
4. message_body
5. sent_at

## Relationships Explained
User to Property:
One-to-Many (1 User can host multiple Properties)

User to Booking:
One-to-Many (1 User can make multiple Bookings)

Property to Booking:
One-to-Many (1 Property can have multiple Bookings)

Booking to Payment:
One-to-One (1 Booking can have 1 Payment)

Property to Review:
One-to-Many (1 Property can have multiple Reviews)

User to Review:
One-to-Many (1 User can write multiple Reviews)

User to Message:
One-to-Many (1 User can send multiple Messages)