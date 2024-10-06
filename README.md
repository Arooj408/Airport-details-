
import java.util.Scanner;

public class AirportSeatManagement {
    static final int ROWS = 5; // Number of rows in the plane
    static final int COLUMNS = 5; // Number of seats per row
    static String[][] seats = new String[ROWS][COLUMNS]; // Array to represent seats

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        initializeSeats(); // Initialize the seating chart with empty seats
        
        int choice;
        do {
            System.out.println("\n--- Airport Seat Management System ---");
            System.out.println("1. Display Seating Chart");
            System.out.println("2. Book a Seat");
            System.out.println("3. Cancel a Booking");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            
            switch (choice) {
                case 1:
                    displaySeats();
                    break;
                case 2:
                    bookSeat(scanner);
                    break;
                case 3:
                    cancelBooking(scanner);
                    break;
                case 4:
                    System.out.println("Exiting system. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice, please try again.");
            }
        } while (choice != 4);
        
        scanner.close(); // Close the scanner object
    }

    // Initialize the seating chart with empty seats
    public static void initializeSeats() {
        for (int i = 0; i < ROWS; i++) {
            for (int j = 0; j < COLUMNS; j++) {
                seats[i][j] = "Empty"; // Mark all seats as empty
            }
        }
    }

    // Display the current seating chart
    public static void displaySeats() {
        System.out.println("\nCurrent Seating Chart:");
        for (int i = 0; i < ROWS; i++) {
            for (int j = 0; j < COLUMNS; j++) {
                System.out.print(seats[i][j] + "\t");
            }
            System.out.println(); // Move to the next row
        }
    }

    // Book a seat by specifying the row and seat number
    public static void bookSeat(Scanner scanner) {
        System.out.print("Enter row number (1 to " + ROWS + "): ");
        int row = scanner.nextInt() - 1; // Adjust for array index
        System.out.print("Enter seat number (1 to " + COLUMNS + "): ");
        int seat = scanner.nextInt() - 1;

        if (row >= 0 && row < ROWS && seat >= 0 && seat < COLUMNS) {
            if (seats[row][seat].equals("Empty")) {
                seats[row][seat] = "Booked"; // Mark seat as booked
                System.out.println("Seat booked successfully.");
            } else {
                System.out.println("Seat already booked.");
            }
        } else {
            System.out.println("Invalid seat selection.");
        }
    }

    // Cancel a booking by specifying the row and seat number
    public static void cancelBooking(Scanner scanner) {
        System.out.print("Enter row number (1 to " + ROWS + "): ");
        int row = scanner.nextInt() - 1; // Adjust for array index
        System.out.print("Enter seat number (1 to " + COLUMNS + "): ");
        int seat = scanner.nextInt() - 1;

        if (row >= 0 && row < ROWS && seat >= 0 && seat < COLUMNS) {
            if (seats[row][seat].equals("Booked")) {
                seats[row][seat] = "Empty"; // Mark seat as empty
                System.out.println("Booking cancelled successfully.");
            } else {
                System.out.println("Seat is not booked.");
            }
        } else {
            System.out.println("Invalid seat selection.");
        }
    }
    
