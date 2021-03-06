# Hashtables

### Terminology:
- Hash - converted string into a value that can be used.
- Hashtable - Used to determine the index of the array.
- Buckets - Contained in each index of the array of the hashtable. 
- Collisions - When more than one key gets hashed to the same location.

### Why do we use them?
- Hold unique values
- Dictionary
- Library

### What Are they?
*Hashtables are a data structure that utilize key value pairs.
- Quickly stores the key and quickly retrieves the value.
- Encodes the key that maps to a specific location for value
- Uses O(1) time complexity.

### Structure
*Hashing
- Hash codes should never have randomness to them. 
- The same key should always produce the same hash code.

### Creating a Hash
- Made from an array. 
- After array creation turn the “key” into a numeric number value
- Each Index contains “buckets”. 
- Each “bucket” holds one key/value pair. 
- The hashtable starts empty and overwrites the value once a key generates a hashCode
---
> Add or multiply all the ASCII values together.
> Multiply it by a prime number such as 599.
> Use modulo to get the remainder of the result, when divided by the total size of the array.
> Insert into the array at that index.

Example:
```
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16
```
> Key gets placed in index of 16. 
> We now know that our key Cat maps to index 16 of the array. 
> We can view into this index and find “Josie”, our value quickly.
---

### Collisions
- Occurs when another key hashes to the same index. 
- A “perfect hash” will never have any collisions. 
- The hash map nmust handle two keys resolving to the same index.
- Collisions are solved by initializing a LinkedList.

**Hash maps do this to store values:

1. accept a key
1. calculate the hash of the key
1. use modulus to convert the hash into an array index
1. store the key with the value by appending both to the end of a linked list

**Hash maps do this to read value:

1. accept a key
1. calculate the hash of the key
1. use modulus to convert the hash into an array index
1. use the array index to access the short LinkedList representing a bucket
1. search through the bucket looking for a node with a key/value pair that matches the key you were given

### Hash Code Examples
**Calculating hashes and indexes by summing the ascii values of each character:**
```
SUM HASHED: Pioneer Square = 1379
SUM HASHED: Alki Beach = 884
SUM HASHED: U District = 955

BUCKET SIZE=99
SUM INDEX: 1379 % 99 = 92
SUM INDEX:  884 % 99 = 92
SUM INDEX:  995 % 99 = 64
```
**Calculating hashes and indexes by multiplying the ascii values of each character:**
```
MULT HASHED: Pioneer Square = 599126016
MULT HASHED: Alki Beach = 1062823936
MULT HASHED: U District = 578867200

BUCKET SIZE=99
MULT INDEX:  599126016 % 99 = 93
MULT INDEX: 1062823936 % 99 = 31
MULT INDEX:  578867200 % 99 = 43
```

### Bucket Sizes
- Hash Maps can have any number of buckets. 
- If a hash map has only a few buckets it will be densely full and have many collisions.
- If a hash map has more buckets it will be more sparsely populated, there will be less collisions.
- The load factor tells us something about how full the hash table is. 
- Can recognize when too full and automatically add more buckets to accommodate more data.
---
### Here’s what the same information looks like in two different hash tables. 
- The first hash table only has 7 buckets. 
- The second has 100 buckets.

**7 buckets:**
```
Bucket 0: [{Renton: 98055} --> {Capital Hill: 98102} --> {Greenwood: 98103} --> {Greenlake: 98103} --> {Pioneer Square: 98104} --> {University District: 98105} --> {Columbia City: 98118}]
Bucket 1: [{Bellevue: 98005} --> {Seattle: 98101}]
Bucket 2: [{Mercer Island: 98040} --> {Alki Beach: 98116} --> {Northgate: 98125}]
Bucket 3: [{Downtown: 98101} --> {Laurelhurst: 98105} --> {Bainbridge Island: 98110} --> {Magnolia: 98199}]
Bucket 4: [{Kirkland: 98033} --> {Lynnwood: 98037} --> {Ballard: 98107} --> {Queen Anne: 98109} --> {West Seattle: 98116}]
Bucket 5: [{International District: 98104} --> {Mount Baker:98144}]
Bucket 6: [{Redmond: 98052} --> {Freemont: 98103} --> {South Lake Union: 98109} --> {Madrona: 98110} --> {Belltown: 98121}]
```
**100 buckets:**
```
Bucket 0: []
Bucket 1: []
Bucket 2: []
Bucket 3: []
Bucket 4: []
Bucket 5: []
Bucket 6: []
Bucket 7: []
Bucket 8: []
Bucket 9: []
Bucket 10: []
Bucket 11: []
Bucket 12: [{South Lake Union: 98109}]
Bucket 13: [{Madrona: 98110}]
Bucket 14: []
Bucket 15: []
Bucket 16: [{Magnolia:98199}]
Bucket 17: []
Bucket 18: []
Bucket 19: [{Greenlake:98103}]
Bucket 20: [{Redmond:98052}]
Bucket 21: []
Bucket 22: []
Bucket 23: []
Bucket 24: [{Kirkland:98033}]
Bucket 25: []
Bucket 26: []
Bucket 27: []
Bucket 28: [{Bellevue:98005}]
Bucket 29: [{Seattle:98101}]
Bucket 30: []
Bucket 31: []
Bucket 32: []
Bucket 33: []
Bucket 34: []
Bucket 35: []
Bucket 36: [{Renton:98055}]
Bucket 37: [{Queen Anne:98109}]
Bucket 38: [{Capital Hill:98102}]
Bucket 39: []
Bucket 40: [{Freemont:98103}]
Bucket 41: []
Bucket 42: []
Bucket 43: []
Bucket 44: []
Bucket 45: []
Bucket 46: []
Bucket 47: [{Greenwood:98103}  --> {Belltown:98121}]
Bucket 48: []
Bucket 49: [{Northgate:98125}]
Bucket 50: [{Bainbridge Island:98110}]
Bucket 51: []
Bucket 52: []
Bucket 53: [{Mercer Island:98040}]
Bucket 54: []
Bucket 55: []
Bucket 56: []
Bucket 57: []
Bucket 58: [{Mount Baker:98144}]
Bucket 59: []
Bucket 60: [{International District:98104}]
Bucket 61: []
Bucket 62: []
Bucket 63: []
Bucket 64: []
Bucket 65: [{Columbia City:98118}]
Bucket 66: [{Lynnwood:98037}]
Bucket 67: []
Bucket 68: []
Bucket 69: []
Bucket 70: []
Bucket 71: []
Bucket 72: [{Downtown:98101}]
Bucket 73: []
Bucket 74: []
Bucket 75: []
Bucket 76: []
Bucket 77: []
Bucket 78: []
Bucket 79: [{University District:98105}]
Bucket 80: []
Bucket 81: []
Bucket 82: []
Bucket 83: []
Bucket 84: [{West Seattle:98116}]
Bucket 85: []
Bucket 86: []
Bucket 87: []
Bucket 88: []
Bucket 89: []
Bucket 90: [{Laurelhurst:98105}]
Bucket 91: []
Bucket 92: [{Pioneer Square: 98104} --> {Alki Beach:98116}]
Bucket 93: []
Bucket 94: []
Bucket 95: []
Bucket 96: [{Ballard:98107}]
Bucket 97: []
Bucket 98: []
```

### Internal Methods
**Add()**

- send the key to the GetHash method.
- go to the index of where it should be placed, 
- Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
- If something does exist, add the new key/value pair to the data structure within that bucket.

**Find()**
- The Find takes in a key, gets the Hash, and goes to the index location specified. 
- Once at the index location is found in the array, it is then the responsibility of the algorithm the iterate through the bucket and see if the key exists and return the value.

**Contains()**
- The Contains method will accept a key, and return a bool on if that key exists inside the hashtable. 
The best way to do this is to have the contains call the GetHash and check the hashtable if the key exists in the table given the index returned.

**GetHash()**
- The GetHash will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.
---
