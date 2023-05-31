# 705. Design HashSet

## Approach
 - Initialize a fixed-size array (bucket) to store the elements of the HashSet.
 - Implement a hashing function to map the keys to specific indices in the bucket.
 - Handle collisions (i.e., multiple keys mapping to the same index) by using separate chaining. Each index of the bucket will contain a linked list or a similar data structure to store the elements with the same hash value.
 - For adding an element, calculate the hash value of the key and insert it into the corresponding bucket if it doesn't already exist.
 - For removing an element, calculate the hash value of the key, find the corresponding bucket, and remove the element from it if it exists.
 - For checking if an element exists, calculate the hash value of the key, find the corresponding bucket, and check if the element is present in it.

<br></br>

## Python Code:
```shell
class MyHashSet:
    def __init__(self):
        self.size = 1000
        self.buckets = [[] for _ in range(self.size)]

    def add(self, key: int) -> None:
        index = self._hash(key)
        if key not in self.buckets[index]:
            self.buckets[index].append(key)

    def remove(self, key: int) -> None:
        index = self._hash(key)
        if key in self.buckets[index]:
            self.buckets[index].remove(key)

    def contains(self, key: int) -> bool:
        index = self._hash(key)
        return key in self.buckets[index]

    def _hash(self, key: int) -> int:
        return key % self.size
```
