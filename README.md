# AirLinesManagementSystem
This is totally dependent on Airlines Management System. And also have some information about that.
import json
import os

FLIGHT_FILE = 'flights.json'
BOOKING_FILE = 'bookings.json'


def load_data(file):
    if os.path.exists(file):
        with open(file, 'r') as f:
            return json.load(f)
    return []


def save_data(file, data):
    with open(file, 'w') as f:
        json.dump(data, f, indent=4)


def add_flight():
    flights = load_data(FLIGHT_FILE)
    flight = {
        "id": input("Enter Flight ID: "),
        "name": input("Enter Airline Name: "),
        "source": input("Enter Source City: "),
        "destination": input("Enter Destination City: "),
        "seats": int(input("Enter Total Seats: "))
    }
    flights.append(flight)
    save_data(FLIGHT_FILE, flights)
    print("✅ Flight added successfully.\n")


def view_flights():
    flights = load_data(FLIGHT_FILE)
    if not flights:
        print("❌ No flights available.\n")
        return
    print("\nAvailable Flights:")
    for f in flights:
        print(f"ID: {f['id']}, {f['name']} - {f['source']} ➡ {f['destination']}, Seats: {f['seats']}")
    print()


def book_ticket():
    flights = load_data(FLIGHT_FILE)
    bookings = load_data(BOOKING_FILE)

    flight_id = input("Enter Flight ID to book: ")
    flight = next((f for f in flights if f['id'] == flight_id), None)

    if not flight:
        print("❌ Flight not found.\n")
        return
    if flight['seats'] <= 0:
        print("⚠️ No seats available on this flight.\n")
        return

    name = input("Enter Passenger Name: ")
    seat_no = flight['seats']

    booking = {
        "flight_id": flight_id,
        "passenger": name,
        "seat_no": seat_no
    }

    bookings.append(booking)
    flight['seats'] -= 1

    save_data(BOOKING_FILE, bookings)
    save_data(FLIGHT_FILE, flights)

    print(f"✅ Ticket Booked! Seat No: {seat_no
    
