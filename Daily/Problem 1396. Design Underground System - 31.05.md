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

<br></br>
## python Code:
```shell
class UndergroundSystem:
    def __init__(self):
        # Dictionary to store total travel time and count for each (start_station, end_station) pair
        self.travel_times = {}

        # Dictionary to store check-in information with customer_id as key and (start_station, check_in_time) as value
        self.check_ins = {}

    def checkIn(self, id: int, stationName: str, t: int) -> None:
        self.check_ins[id] = (stationName, t)

    def checkOut(self, id: int, stationName: str, t: int) -> None:
        start_station, check_in_time = self.check_ins.pop(id)
        travel = (start_station, stationName)
        travel_time = t - check_in_time

        if travel in self.travel_times:
            total_time, count = self.travel_times[travel]
            self.travel_times[travel] = (total_time + travel_time, count + 1)
        else:
            self.travel_times[travel] = (travel_time, 1)

    def getAverageTime(self, startStation: str, endStation: str) -> float:
        travel = (startStation, endStation)
        total_time, count = self.travel_times[travel]
        return total_time / count
```
