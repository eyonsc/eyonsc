#include <stdio.h>
#include <string.h>

int main() {
    int card, origin, destination;
    int continueLoop = 1;
    float discountRate;
    float total_fare = 0.0;
    float tix_fare = 0.0;

    // Fare arrays (Single Journey and Stored Value)
    int single_journey_fares[20][20] = {
        {0, 15, 15, 20, 20, 20, 20, 20, 25, 25, 25, 25, 25, 30, 30, 30, 30, 30, 35, 35}, // BACLARAN
        {15, 0, 15, 15, 20, 20, 20, 20, 25, 25, 25, 25, 25, 25, 30, 30, 30, 30, 35, 35}, // EDSA
        {15, 15, 0, 15, 15, 20, 20, 20, 20, 25, 25, 25, 25, 25, 25, 30, 30, 30, 35, 35}, // LIBERTAD
        {20, 15, 15, 0, 15, 20, 20, 20, 20, 20, 25, 25, 25, 25, 25, 25, 30, 30, 30, 35}, // GIL PUYAT
        {20, 15, 15, 15, 0, 15, 15, 20, 20, 20, 20, 20, 25, 25, 25, 25, 25, 30, 30, 35}, // VITO CRUZ
        {20, 20, 20, 20, 15, 0, 15, 15, 20, 20, 20, 20, 20, 25, 25, 25, 25, 25, 30, 30}, // QUIRINO
        {20, 20, 20, 20, 15, 15, 0, 15, 20, 20, 20, 20, 20, 20, 25, 25, 25, 25, 30, 30}, // PEDRO GIL
        {20, 20, 20, 20, 20, 15, 15, 0, 15, 20, 20, 20, 20, 20, 20, 25, 25, 25, 30, 30}, // UN AVENUE
        {25, 25, 20, 20, 20, 20, 20, 15, 0, 15, 15, 20, 20, 20, 20, 20, 25, 25, 25, 30}, // CENTRAL
        {25, 25, 25, 20, 20, 20, 20, 20, 15, 0, 15, 15, 20, 20, 20, 20, 20, 25, 25, 30}, // CARRIEDO
        {25, 25, 25, 25, 20, 20, 20, 20, 15, 15, 0, 15, 15, 20, 20, 20, 20, 20, 25, 25}, // D. JOSE
        {25, 25, 25, 25, 20, 20, 20, 20, 20, 15, 15, 0, 15, 15, 20, 20, 20, 20, 25, 25}, // BAMBANG
        {25, 25, 25, 25, 25, 20, 20, 20, 20, 20, 15, 15, 0, 15, 15, 20, 20, 20, 25, 25}, // TAYUMAN
        {30, 25, 25, 25, 25, 25, 20, 20, 20, 20, 20, 15, 15, 0, 15, 15, 20, 20, 20, 25}, // BLUMENTRITT
        {30, 30, 25, 25, 25, 25, 25, 20, 20, 20, 20, 20, 15, 15, 0, 15, 15, 20, 20, 25}, // ABAD SANTOS
        {30, 30, 30, 25, 25, 25, 25, 25, 20, 20, 20, 20, 20, 15, 15, 0, 15, 15, 20, 25}, // R. PAPA
        {30, 30, 30, 30, 25, 25, 25, 25, 20, 20, 20, 20, 20, 20, 15, 15, 0, 15, 20, 20}, // 5TH AVENUE
        {30, 30, 30, 30, 30, 25, 25, 25, 25, 25, 20, 20, 20, 20, 20, 20, 15, 0, 20, 20}, // MONUMENTO
        {35, 35, 35, 30, 30, 30, 30, 30, 25, 25, 25, 25, 25, 20, 20, 20, 20, 20, 0, 20}, // BALINTAWAK
        {35, 35, 35, 35, 35, 30, 30, 30, 30, 30, 25, 25, 25, 25, 25, 25, 20, 20, 20, 0}  // FERNANDO POE JR.
    };

     int stored_value_fares[20][20] = {
        {0, 14, 15, 16, 17, 18, 19, 20, 22, 23, 23, 24, 25, 26, 27, 28, 29, 30, 33, 35}, // BACLARAN
        {14, 0, 15, 15, 17, 18, 19, 20, 21, 22, 23, 24, 24, 25, 26, 27, 28, 29, 32, 34}, // EDSA
        {15, 15, 0, 14, 15, 16, 17, 18, 20, 21, 22, 22, 23, 24, 25, 26, 27, 28, 31, 33}, // LIBERTAD
        {16, 15, 14, 0, 15, 16, 17, 17, 19, 20, 21, 21, 22, 23, 24, 25, 26, 27, 30, 32}, // GIL PUYAT
        {17, 17, 15, 15, 0, 14, 15, 16, 18, 19, 19, 20, 21, 22, 23, 24, 25, 26, 29, 31}, // VITO CRUZ
        {18, 18, 16, 16, 14, 0, 14, 15, 17, 18, 18, 19, 20, 21, 22, 23, 24, 25, 28, 30}, // QUIRINO
        {19, 19, 17, 17, 15, 14, 0, 14, 16, 17, 17, 18, 19, 20, 21, 22, 23, 24, 27, 29}, // PEDRO GIL
        {20, 20, 18, 17, 16, 15, 14, 0, 15, 16, 16, 17, 18, 19, 20, 21, 22, 23, 26, 28}, // UN AVENUE
        {22, 21, 20, 19, 18, 17, 16, 15, 0, 14, 15, 16, 17, 18, 19, 20, 21, 22, 25, 27}, // CENTRAL
        {23, 22, 21, 20, 19, 18, 17, 16, 14, 0, 14, 15, 16, 17, 18, 19, 20, 21, 24, 26}, // CARRIEDO
        {23, 23, 22, 21, 19, 18, 17, 16, 15, 14, 0, 14, 15, 16, 17, 18, 19, 20, 23, 25}, // D. JOSE
        {24, 24, 22, 21, 20, 19, 18, 17, 16, 15, 14, 0, 14, 15, 16, 17, 18, 19, 22, 24}, // BAMBANG
        {25, 25, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 0, 14, 15, 16, 17, 18, 21, 23}, // TAYUMAN
        {26, 26, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 0, 14, 15, 16, 17, 20, 22}, // BLUMENTRITT
        {27, 27, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 0, 14, 15, 16, 19, 21}, // ABAD SANTOS
        {28, 28, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 0, 14, 15, 18, 20}, // R. PAPA
        {29, 29, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 0, 14, 17, 19}, // 5TH AVENUE
        {30, 30, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 0, 16, 18}, // MONUMENTO
        {33, 32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 0, 16}, // BALINTAWAK
        {35, 34, 33, 32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 16, 0}  // FERNANDO POE JR.
    };

    int lastDestination = -1;

    while (continueLoop) {
        printf("==========================\n");
        printf("     Fare Calculator    \n");
        printf("==========================\n");

        printf("Please select the type of card you have:\n");
        printf(" 1. Regular\n");
        printf(" 2. Student\n");
        printf(" 3. PWD/Senior\n");
        printf("Enter your choice (1-3): ");
        scanf("%d", &card);
        
        // Set discount based on card type
        switch (card) {
            case 1: // Regular
                discountRate = 0.0; // 0% discount
                break;
            case 2: // Student
                discountRate = 0.20; // 20% discount
                break;
            case 3: // PWD/Senior
                discountRate = 0.30; // 30% discount
                break;
            default:
                printf("Invalid card type selected.\n");
                return 1; // Exit with an error code
        }

        printf("\nSelect card type for fare calculation:\n");
        printf(" 1. Single Journey\n");
        printf(" 2. Stored Value\n");
        printf("Enter your choice (1-2): ");
        scanf("%d", &card);
        
        if (card != 1 && card != 2) {
            printf("Invalid card type. Please enter 1 for Single Journey or 2 for Stored Value.\n");
            continue; // Restart loop for valid input
        }

        // Set the origin to the last destination if it exists
        if (lastDestination != -1) {
            origin = lastDestination; // Set the previous destination as the initial origin
            printf("Using last destination (%d) as the initial origin.\n", lastDestination);
        } else {
            printf("\nSelect your origin station:\n");
        printf("---------------------------------------------------\n");
        printf("| Station No. | Station Name                      |\n");
        printf("---------------------------------------------------\n");
        printf("|     1       | Baclaran                          |\n");
        printf("|     2       | EDSA                              |\n");
        printf("|     3       | Libertad                          |\n");
        printf("|     4       | Gil Puyat                         |\n");
        printf("|     5       | Vito Cruz                         |\n");
        printf("|     6       | Quirino                           |\n");
        printf("|     7       | Pedro Gil                         |\n");
        printf("|     8       | Un Avenue                         |\n");
        printf("|     9       | Central                           |\n");
        printf("|     10      | Carriedo                          |\n");
        printf("|     11      | D. Jose                           |\n");
        printf("|     12      | Bambang                           |\n");
        printf("|     13      | Tayuman                           |\n");
        printf("|     14      | Blumentritt                       |\n");
        printf("|     15      | Abad Santos                       |\n");
        printf("|     16      | R. Papa                           |\n");
        printf("|     17      | 5th Avenue                        |\n");
        printf("|     18      | Monumento                         |\n");
        printf("|     19      | Balintawak                        |\n");
        printf("|     20      | Fernando Poe Jr.                  |\n");
        printf("---------------------------------------------------\n");
            printf("Enter your origin station (1-20): ");
            scanf("%d", &origin);
        }
        
        printf("Enter your destination station (1-20): ");
        scanf("%d", &destination);

        // Ensure origin and destination are valid
        if (origin < 1 || origin > 20 || destination < 1 || destination > 20) {
            printf("Invalid station numbers. Please enter numbers between 1 and 20.\n");
            continue; // Restart loop for valid input
        }
        
        origin -= 1;
        destination -= 1; 
        
        // Calculate fare based on card type
        if (card == 1) {
            tix_fare = single_journey_fares[origin][destination];
        } else if (card == 2) {
            tix_fare = stored_value_fares[origin][destination];
        }

        // Apply discount
        tix_fare = tix_fare * (1 - discountRate);
        total_fare += tix_fare;

        printf("\n---------------------------------------------------\n");
        printf(" Your Fare is: %.2f\n", tix_fare);
        printf("---------------------------------------------------\n");

        // Store the last destination for the next loop iteration
        lastDestination = destination + 1; // Save it as 1-based index

        printf("Do you want to enter another trip? (1 for Yes, 0 for No): ");
        scanf("%d", &continueLoop);
    }

    printf("\n===============================================\n");
    printf(" Total Fare after discount: %.2f\n", total_fare);
    printf("===============================================");
    return 0;
}
