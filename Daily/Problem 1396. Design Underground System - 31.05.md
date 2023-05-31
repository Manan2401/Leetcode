# 1396. Design Underground System

## Approach:
To design the "Underground System," we can use two data structures: one to store the check-in information and another to store the travel times. Here is the overall approach:

 - For check-in:
   - When a customer checks in, store their ID along with the station name and check-in time in a dictionary or map. This will allow us to retrieve the check-in information later when the customer checks out.
 - For check-out:
   - When a customer checks out, retrieve their check-in information from the dictionary using their ID.
   - Calculate the travel time by subtracting the check-in time from the current check-out time.
 - Update the travel times dictionary:
   - If the (start_station, end_station) pair already exists in the dictionary, update the total time and increment the count.
   - Otherwise, create a new entry in the dictionary with the initial travel time and count.
 - For calculating average travel time:
   - Retrieve the total time and count from the travel times dictionary for the given (startStation, endStation) pair.
   - Calculate and return the average travel time by dividing the total time by the count.
