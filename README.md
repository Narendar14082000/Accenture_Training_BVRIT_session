# Accenture_Training_BVRIT_session

```
import java.util.*;  // Importing the necessary library for Scanner and other utilities.

class Main {
  
  /**
   * Function to calculate the minimum number of houses required 
   * to provide enough food for all the rats.
   * 
   * @param r: Number of rats in the area.
   * @param unit: Food units each rat consumes.
   * @param arr: Array representing the amount of food in each house.
   * @param n: Total number of houses.
   * @return The number of houses required to meet the food requirement, or -1/0 based on conditions.
   */
  public static int solve(int r, int unit, int arr[], int n) {
    // Return -1 if the input array is null.
    if (arr == null) return -1;

    // Calculate the total amount of food needed for all rats.
    int res = r * unit;  // res stores r * unit (total food required).

    // Variables to store the cumulative food sum and the house count.
    int sum = 0, count = 0;

    // Loop through the food array to accumulate the food from each house.
    for (int i = 0; i < n; i++) {
      sum += arr[i];  // Add the food from the current house to the sum.
      count++;        // Increment the house count.

      // If the accumulated food is enough for all rats, stop the loop.
      if (sum >= res) break;
    }

    // If even after visiting all houses, the food is not enough, return 0.
    if (sum < res) return 0;

    // Return the number of houses required to meet the food requirement.
    return count;
  }

  public static void main(String[] args) {
    // Create a Scanner object to read input from the user.
    Scanner sc = new Scanner(System.in);

    // Check if the input contains an integer to avoid input errors.
    if (sc.hasNextInt()) {
      // Read the number of rats from the user.
      int r = sc.nextInt();
      
      // Read the food units consumed by each rat.
      int unit = sc.nextInt();
      
      // Read the number of houses.
      int n = sc.nextInt();

      // Initialize the array to store food quantities for each house.
      int arr[] = new int[n];

      // Loop to read food quantities for each house.
      for (int i = 0; i < n; i++) {
        // Ensure the input has an integer before reading to avoid exceptions.
        if (sc.hasNextInt()) {
          arr[i] = sc.nextInt();  // Store the food quantity in the array.
        } else {
          // If input is missing, print an error message and exit.
          System.out.println("Not enough input provided.");
          return;
        }
      }

      // Call the solve function and print the result.
      System.out.println(solve(r, unit, arr, n));
    } else {
      // If the input is invalid, print an error message.
      System.out.println("Invalid input.");
    }

    // Close the Scanner to release resources.
    sc.close();
  }
}
```
