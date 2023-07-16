# Section 7: 07 - Data Structures Hash Tables

## 75-001 Hash Tables Introduction
Hash tables = hash maps, maps(java), unordered maps, dictionaries(python), objects(js) and hashes(ruby) and ... . There are many ways to call this DS.
You see these in DBs, caches and ... .


## 76-002 Hash Function
A hash function(the black box) is a function that generates a value of fixed length for each input that it gets. If we give it the same input, it's gonna give me the
same output. But we have no idea how to convert the result back into the input. We call this **idempotent** which means that a function, given an input,
always outputs the same output. The one benefit and why we would want to use this in a DS, is that we get fast data access. Because all we have to do to find for example
`basket.grapes`, is to pass grapes to sth like an md5 hash generator and we immediately know where it is in our memory on our computer. Note: The returned hash from
hash generator doesn't look like an address. Right?

A: Technically, a hash function that we use for hash tables, is gonna take `grapes` in `basket.grapes`, generate a hash and then convert it to an index space or an address space 
that is has based on that generated hash.

Everytime you add a property to memory or retrieve a property from memory(both times we're sending the key to the hash function to find where to get the value of it from),
we need the hash function to be fast(O(1)).

Hash functions like sha256 take a long time to generate a hash and it's an overly complex hashing function that is used a lot in cryptography.

## 77-003 Hash Collisions
When you have a collision(two or more keys(with their values obviously) go into the same address space), it slows down reading and writing with a hash table 
with `O(n/k)` where k is the size of your hash table and by removing constants, it becomes `O(n)` operation.

Key-value pairs creates sth called a bucket in hash tables.

There are three common ways to deal with these collisions:
1) With linked lists(separate chaining)
2) open addressing
3) robin-hood hashing

So when we talk about fast lookups in hash tables, occasionally, depending on the hash function, it might take O(n) in contrast to default O(1).

## 78-004 Hash Tables In Different Languages
In js, with `Map`, we can use any data type as the key and it also maintains the insertion order. But with an object, there is no order. In objects, our data
is inserted randomly in different places of memory. But there are some versions of hash tables like maps in JS that maintains this order of insertion, so that when we
loop through items in an map, we have this maintained order.

Set is similar to Map, the only difference is that it only stores the keys, no values.

## 79-005 Exercise Implement A Hash Table
## 80-006 Solution Implement A Hash Table
TODO

## 81-007 keys()
TODO
## 82-008 Extra keys() Without Collision
Look at the attached file.

## 83-009 Hash Tables VS Arrays_en
Hash tables are great when you want quick access to certain values. Remember that searching through an array for an item takes a long time, we have to
loop through every item and see if the element we want is that one or not, but with hash tables that's really fast and this is why hash tables are used in DBs,
because we want to search for sth in a DB and it gives it back to us right away. 

Inserting items in a hash table unlike an array that might shift indexes, is **typically** O(1). You just have to hash and create the key. Although
we have those cases of collision, most of the time, that's sth that we don't need to worry about too much and we can assume an insert of O(1).

A problem of hash tables was the idea of no concept of order. In arrays, each item was placed next to each other in memory. Hash tables are kinda placed all over
the place!

## 84-010 Exercise First Recurring Character
## 85-011 Solution First Recurring Character
## 86-012 Interesting Tidbit Python Dictionaries
File attached.

## 87-013 Hash Tables Review

```js
class HashTable {
  constructor(size){
    this.data = new Array(size);
    // this.data = [];
  }

  _hash(key) {
    let hash = 0;
    for (let i =0; i < key.length; i++){
        hash = (hash + key.charCodeAt(i) * i) % this.data.length
    }
    return hash;
  }

  set(key, value) {
    let address = this._hash(key);
    if (!this.data[address]) {
      this.data[address] = [];
    }
    this.data[address].push([key, value]);
    return this.data;
  }

  get(key){
    const address = this._hash(key);
    const currentBucket = this.data[address]
    if (currentBucket) {
      for(let i = 0; i < currentBucket.length; i++){
        if(currentBucket[i][0] === key) {
          return currentBucket[i][1]
        }
      }
    }
    return undefined;
  }
  
  keys(){
    const keysArray = [];
    console.log(this.data.length);
    for (let i = 0; i < this.data.length; i++){
      if(this.data[i]){
        keysArray.push(this.data[i][0][0])
      }
    }
    return keysArray;
  }
}

const myHashTable = new HashTable(50);
myHashTable.set('grapes', 10000)
myHashTable.set('grapes', 10000)
myHashTable.get('grapes')
myHashTable.set('apples', 9)
myHashTable.get('apples')
myHashTable.keys()
```

002 MD5
http://www.miraclesalad.com/webtools/md5.php

003 Hash-Table-Animation
https://www.cs.usfca.edu/~galles/visualization/OpenHash.html

003 Hash-Tables-Wikipedia
https://en.wikipedia.org/wiki/Hash_table

004 Hash-Tables-also-called-Associative-Arrays-in-other-languages
https://en.wikipedia.org/wiki/Comparison_of_programming_languages_(associative_array)

004 Hash-Table-Repl
https://repl.it/@aneagoie/DataStructures-Hash-Tables

005 Exercise-Hash-Tables-Repl
https://repl.it/@aneagoie/DataStructures-Hash-Table-exercise

006 Solution-Code
https://repl.it/@aneagoie/DataStructures-Hash-Table-Implementation-1

007 Solution-Code
https://repl.it/@aneagoie/DataStructures-Hash-Table-Implementation

010 Find-First-Recurring-Character
https://repl.it/@aneagoie/firstRecurringCharacter-exercise

011 Solution-Code
https://repl.it/@aneagoie/firstRecurringCharacter

013 Technical-Interview-Mind-Map
https://coggle.it/diagram/W5E5tqYlrXvFJPsq/t/master-the-interview
