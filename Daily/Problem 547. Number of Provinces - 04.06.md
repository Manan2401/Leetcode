# 547. Number of Provinces

## Approach:
 - Initialize the variable visited to an empty set.
 - Define a function called dfs that takes the input isConnected, visited, and i.
 - Check if i is already in the visited set. If it is, return 0.
 - Add i to the visited set.
 - Loop through isConnected[i] to check if there are any direct connections between i and j.
 - If there is a direct connection between i and j, call the dfs function recursively on j.
 - Return 1 to represent the current province.
 - Initialize the variable provinces to 0.
 - Loop through the length of isConnected to check all the cities.
 - For each city, call the dfs function on it and add the result to provinces.
 - Return provinces as the total number of provinces.

<br></br>
## Python Code:
 ```shell
 
 ```
