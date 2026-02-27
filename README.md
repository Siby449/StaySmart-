# StaySmart
StaySmart

StaySmart is a Django-based hotel room booking system that allows users to create rooms, view available rooms, and make bookings. The system ensures data integrity, validation, and user-specific booking views.

Features
Rooms Management

Users (or admins) can create, edit, and delete rooms.

Each room has:

Name

Room type (e.g., Single, Double, Suite)

Price per night

Description

Availability status

Only existing rooms can be booked, enforcing proper workflow.

Booking System

Users can book a room for specific dates.

The system calculates total price automatically based on:

Number of nights

Room price per night

Bookings include:

User reference

Room reference

Check-in and check-out dates

Total price

Validations:

Check-out date must be after check-in date

Overlapping bookings for the same room are prevented

Users can view, edit, and cancel only their own bookings.

User Authentication

Only authenticated users can make bookings or view the dashboard.

Unauthenticated users are redirected to the login page.

Templates & Workflow

Room Management

room_form.html → Add or edit a room

room_list.html → List all rooms with availability

room_detail.html → View room details and access “Book This Room” button

room_confirm_delete.html → Delete a room confirmation

Booking Management

booking_form.html → Book or edit an existing room

booking_list.html → User’s bookings

booking_detail.html → Booking details view

booking_confirm_delete.html → Cancel booking confirmation

Workflow

Create room (must exist first)

List and view room details

Book available rooms

View, edit, or cancel user-specific bookings

Backend

Django 6.0.2

Models:

Room → Stores room details

Booking → Stores booking details with validation for overlapping and date correctness

Views:

Class-based views for CRUD operations

Booking creation requires passing the room object

URL structure:

rooms: → Room CRUD URLs

bookings: → Booking CRUD URLs

Validations

Date Validation: Check-out must be after check-in

Overlap Prevention: Same room cannot be double-booked for overlapping dates

Total Price Calculation: Based on room price × number of nights

User Access Control: Users can only view their own bookings

Testing

The project includes unit tests for bookings:

Booking creation → Checks total price calculation

Invalid date validation → Ensures check-out > check-in

Overlap prevention → Prevents double-booking of the same room

User authentication → Redirects unauthenticated users from dashboard

User-specific bookings → Users can only see their own bookings

Tests are implemented using Django TestCase with setUpTestData for efficiency. Validation errors are tested safely using substring matching to avoid test failures from minor text changes.

Future Improvements

Add room image uploads for better UX

Implement calendar view for available bookings

Allow admin users to manage bookings for all users

Improve front-end styling using Bootstrap
