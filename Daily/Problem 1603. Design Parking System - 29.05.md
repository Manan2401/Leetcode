# 1603. Design Parking System

## Approach:
 - The approach for the "Design Parking System" problem is to maintain a data structure that keeps track of the number of available parking spots for each car type. In this case, we can use a list or an array to store the available spots for big, medium, and small cars.

 - Initialize the parking system: In the constructor or initialization method, store the number of available spots for each car type in the data structure (list or array).

 - Add a car: In the addCar method, check if there is an available spot for the specified car type. If the number of available spots for that car type is greater than 0, decrement the count of available spots for that car type and return true to indicate a successful addition. Otherwise, return false to indicate that no parking spot is available for that car type.

<br></br>
## Python Code:
```shell
class ParkingSystem:
    def __init__(self, big: int, medium: int, small: int):
        self.spots = [big, medium, small]

    def addCar(self, carType: int) -> bool:
        if self.spots[carType - 1] > 0:
            self.spots[carType - 1] -= 1
            return True
        else:
            return False
```
