#include <stdio.h>

void displayStations() {
    printf("========== LRT-2 STATIONS ==========\n\n");
    printf("(1) Recto     (7) Betty Go     (13) Antipolo\n");
    printf("(2) Legarda   (8) Cubao\n");
    printf("(3) Pureza    (9) Anonas\n");
    printf("(4) V. Mapa   (10) Katipunan\n");
    printf("(5) J. Ruiz   (11) Santolan\n");
    printf("(6) Gilmore   (12) Marikina\n\n");
}

int getFare(int origin, int destination) {
    int fare = 0;

    if (origin == destination) {
        return 0;
    }

    switch (origin) {
        case 1:
            if (destination == 2) fare = 15;
            else if (destination == 3) fare = 20;
            else if (destination == 4) fare = 20;
            else if (destination == 5) fare = 20;
            else if (destination == 6) fare = 25;
            else if (destination == 7) fare = 25;
            else if (destination == 8) fare = 25;
            else if (destination == 9) fare = 25;
            else if (destination == 10) fare = 25;
            else if (destination == 11) fare = 30;
            else if (destination == 12) fare = 35;
            else if (destination == 13) fare = 35;
            break;
        case 2:
            if (destination == 1) fare = 15;
            else if (destination == 3) fare = 15;
            else if (destination == 4) fare = 20;
            else if (destination == 5) fare = 20;
            else if (destination == 6) fare = 20;
            else if (destination == 7) fare = 25;
            else if (destination == 8) fare = 25;
            else if (destination == 9) fare = 25;
            else if (destination == 10) fare = 25;
            else if (destination == 11) fare = 30;
            else if (destination == 12) fare = 35;
            else if (destination == 13) fare = 35;
            break;
        case 3:
            if (destination == 1) fare = 20;
            else if (destination == 2) fare = 15;
            else if (destination == 4) fare = 15;
            else if (destination == 5) fare = 20;
            else if (destination == 6) fare = 20;
            else if (destination == 7) fare = 20;
            else if (destination == 8) fare = 25;
            else if (destination == 9) fare = 25;
            else if (destination == 10) fare = 25;
            else if (destination == 11) fare = 30;
            else if (destination == 12) fare = 35;
            else if (destination == 13) fare = 35;
            break;
        case 4:
            if (destination == 1) fare = 20;
            else if (destination == 2) fare = 20;
            else if (destination == 3) fare = 15;
            else if (destination == 5) fare = 15;
            else if (destination == 6) fare = 20;
            else if (destination == 7) fare = 20;
            else if (destination == 8) fare = 20;
            else if (destination == 9) fare = 25;
            else if (destination == 10) fare = 25;
            else if (destination == 11) fare = 30;
            else if (destination == 12) fare = 30;
            else if (destination == 13) fare = 30;
            break;
        case 5:
            if (destination == 1) fare = 20;
            else if (destination == 2) fare = 20;
            else if (destination == 3) fare = 20;
            else if (destination == 4) fare = 15;
            else if (destination == 6) fare = 15;
            else if (destination == 7) fare = 20;
            else if (destination == 8) fare = 20;
            else if (destination == 9) fare = 20;
            else if (destination == 10) fare = 25;
            else if (destination == 11) fare = 25;
            else if (destination == 12) fare = 30;
            else if (destination == 13) fare = 30;
            break;
        case 6:
            if (destination == 1) fare = 25;
            else if (destination == 2) fare = 20;
            else if (destination == 3) fare = 20;
            else if (destination == 4) fare = 20;
            else if (destination == 5) fare = 15;
            else if (destination == 7) fare = 15;
            else if (destination == 8) fare = 20;
            else if (destination == 9) fare = 20;
            else if (destination == 10) fare = 20;
            else if (destination == 11) fare = 25;
            else if (destination == 12) fare = 25;
            else if (destination == 13) fare = 30;
            break;
        case 7:
            if (destination == 1) fare = 25;
            else if (destination == 2) fare = 25;
            else if (destination == 3) fare = 20;
            else if (destination == 4) fare = 20;
            else if (destination == 5) fare = 20;
            else if (destination == 6) fare = 15;
            else if (destination == 8) fare = 15;
            else if (destination == 9) fare = 20;
            else if (destination == 10) fare = 20;
            else if (destination == 11) fare = 25;
            else if (destination == 12) fare = 25;
            else if (destination == 13) fare = 30;
            break;
        case 8:
            if (destination == 1) fare = 25;
            else if (destination == 2) fare = 25;
            else if (destination == 3) fare = 25;
            else if (destination == 4) fare = 20;
            else if (destination == 5) fare = 20;
            else if (destination == 6) fare = 20;
            else if (destination == 7) fare = 15;
            else if (destination == 9) fare = 15;
            else if (destination == 10) fare = 20;
            else if (destination == 11) fare = 25;
            else if (destination == 12) fare = 25;
            else if (destination == 13) fare = 30;
            break;
        case 9:
            if (destination == 1) fare = 25;
            else if (destination == 2) fare = 25;
            else if (destination == 3) fare = 25;
            else if (destination == 4) fare = 25;
            else if (destination == 5) fare = 20;
            else if (destination == 6) fare = 20;
            else if (destination == 7) fare = 20;
            else if (destination == 8) fare = 15;
            else if (destination == 10) fare = 15;
            else if (destination == 11) fare = 20;
            else if (destination == 12) fare = 25;
            else if (destination == 13) fare = 25;
            break;
        case 10:
            if (destination == 1) fare = 25;
            else if (destination == 2) fare = 25;
            else if (destination == 3) fare = 25;
            else if (destination == 4) fare = 25;
            else if (destination == 5) fare = 25;
            else if (destination == 6) fare = 20;
            else if (destination == 7) fare = 20;
            else if (destination == 8) fare = 20;
            else if (destination == 9) fare = 15;
            else if (destination == 11) fare = 15;
            else if (destination == 12) fare = 20;
            else if (destination == 13) fare = 25;
            break;
        case 11:
            if (destination == 1) fare = 30;
            else if (destination == 2) fare = 30;
            else if (destination == 3) fare = 30;
            else if (destination == 4) fare = 30;
            else if (destination == 5) fare = 25;
            else if (destination == 6) fare = 25;
            else if (destination == 7) fare = 25;
            else if (destination == 8) fare = 25;
            else if (destination == 9) fare = 20;
            else if (destination == 10) fare = 15;
            else if (destination == 12) fare = 15;
            else if (destination == 13) fare = 20;
            break;
        case 12:
            if (destination == 1) fare = 35;
            else if (destination == 2) fare = 35;
            else if (destination == 3) fare = 35;
            else if (destination == 4) fare = 30;
            else if (destination == 5) fare = 30;
            else if (destination == 6) fare = 25;
            else if (destination == 7) fare = 25;
            else if (destination == 8) fare = 25;
            else if (destination == 9) fare = 25;
            else if (destination == 10) fare = 20;
            else if (destination == 11) fare = 15;
            else if (destination == 13) fare = 15;
            break;
        case 13:
            if (destination == 1) fare = 35;
            else if (destination == 2) fare = 35;
            else if (destination == 3) fare = 35;
            else if (destination == 4) fare = 30;
            else if (destination == 5) fare = 30;
            else if (destination == 6) fare = 30;
            else if (destination == 7) fare = 30;
            else if (destination == 8) fare = 30;
            else if (destination == 9) fare = 25;
            else if (destination == 10) fare = 25;
            else if (destination == 11) fare = 20;
            else if (destination == 12) fare = 15;
            break;
    }

    return fare;
}

int main() {
    int origin, destination, passengerType, ticketType;
    float discount = 0.0;
    
    displayStations();
    
    printf("\nSelect Passenger Type:\n");
    printf("1 - Regular\n");
    printf("2 - Student\n");
    printf("3 - PWD (Person with Disability)\n");
    printf("\nEnter your choice: ");
    scanf("%d", &passengerType);
    
    if (passengerType == 2 || passengerType == 3) {
        discount = 0.20;
    }

    printf("\nSelect Ticket Type:\n");
    printf("1 - Single Journey Ticket\n");
    printf("2 - Stored Value Card\n");
    printf("\nEnter your choice: ");
    scanf("%d", &ticketType);
    
    printf("\nEnter origin station number: ");
    scanf("%d", &origin);
    
    printf("Enter destination station number: ");
    scanf("%d", &destination);
    
    int fare = getFare(origin, destination);
    
    if (fare > 0 && discount > 0.0) {
        fare -= fare * discount;
    }

    if (fare > 0) {
        if (ticketType == 1) {
            printf("\nFare for Single Journey Ticket from station %d to station %d is %d pesos.\n", origin, destination, fare);
        } else if (ticketType == 2) {
            printf("\nFare for Stored Value Card from station %d to station %d is %d pesos.\n", origin, destination, fare);
        }
    } else if (fare == 0) {
        printf("Origin and destination are the same. No fare required.\n");
    } else {
        printf("Invalid fare calculation.\n");
    }

    return 0;
}
