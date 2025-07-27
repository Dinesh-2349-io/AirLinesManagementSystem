import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Flight {
    String id;
    String name;
    String source;
    String destination;
    int seats;

    public Flight(String id, String name, String source, String destination, int seats) {
        this.id = id;
        this.name = name;
        this.source = source;
        this.destination = destination;
        this.seats = seats;
    }

    @Override
    public String toString() {
        return "Flight ID: " + id + ", " + name + ", From: " + source + " To: " + destination + ", Seats Left: " + seats;
    }
}

class Booking {
    String passengerName;
    String flightId;
    int seatNumber;

    public Booking(String passengerName, String flightId, int seatNumber) {
        this.passengerName = passengerName;
        this.flightId = flightId;
        this.seatNumber = seatNumber;
    }

    @Override
    public String toString() {
        return "Passenger: " + passengerName + ", Flight ID: " + flightId + ", Seat No: " + seatNumber;
    }
}

public class AirlinesManagementSystem {
    static List<Flight> flights = new ArrayList<>();
    static List<Booking> bookings = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        int choice;
        do {
            System.out.println("\n=== Airlines Management System ===");
            System.out.println("1. Add Flight");
            System.out.println("2. View Flights");
            System.out.println
