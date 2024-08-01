Here are two JavaScript problems designed to challenge learners on working with objects, especially focusing on nested structures.

### Problem 1: Print Nested Object Keys

#### Problem Name
**Print Nested Object Keys with Indentation**

#### Problem Description
Given an object that may have nested objects, write a function to print all the keys of the object. The keys of the nested objects should be indented as per their depth. For example, keys in the top-level object should have no indentation, keys in nested objects one level deep should be indented by two spaces, and so on.

#### Solution Approach
To solve this problem, you can use a recursive function that traverses the object. For each level of depth, increment the indentation and recursively call the function for nested objects. Print each key with the appropriate indentation level.

#### Hints
1. Use recursion to traverse through each level of nested objects.
2. Keep track of the current depth and use it to determine the indentation.
3. Base case: When you encounter a value that is not an object, do not recurse further.

#### Code Stub
```javascript
function printObjectKeys(obj, depth = 0) {
    // Add your solution here
}

// Example usage
const sampleObject = {
    key1: 'value1',
    key2: {
        key3: 'value3',
        key4: {
            key5: 'value5'
        }
    },
    key6: 'value6'
};

printObjectKeys(sampleObject);
```

#### Complete Solution
```javascript
function printObjectKeys(obj, depth = 0) {
    for (let key in obj) {
        console.log(' '.repeat(depth * 2) + key);
        if (typeof obj[key] === 'object' && obj[key] !== null) {
            printObjectKeys(obj[key], depth + 1);
        }
    }
}

// Example usage
const sampleObject = {
    key1: 'value1',
    key2: {
        key3: 'value3',
        key4: {
            key5: 'value5'
        }
    },
    key6: 'value6'
};

printObjectKeys(sampleObject);
```

#### Test Cases
```javascript
const testCase1 = {
    a: 1,
    b: {
        c: 2,
        d: {
            e: 3
        }
    },
    f: 4
};

printObjectKeys(testCase1);
// Expected Output:
// a
// b
//   c
//   d
//     e
// f

const testCase2 = {
    x: {
        y: {
            z: {
                a: 1
            }
        }
    }
};

printObjectKeys(testCase2);
// Expected Output:
// x
//   y
//     z
//       a
```

---

### Problem 2: Deep Copy of Object

#### Problem Name
**Deep Copy of Nested Object**

#### Problem Description
Given an object that may contain nested objects, write a function to create a deep copy of the object. The deep copy should not retain any references to the original object's nested objects.

#### Solution Approach
To create a deep copy, iterate through the object's properties. If a property is an object, recursively create a deep copy of that object. If the property is a primitive, directly copy its value. You can use recursion to achieve a deep copy of nested objects.

#### Hints
1. Recursively traverse each object and array.
2. Use recursion to create a copy for nested objects.
3. Handle both arrays and plain objects during recursion.

#### Code Stub
```javascript
function deepCopy(obj) {
    // Add your solution here
}

// Example usage
const originalObject = {
    key1: 'value1',
    key2: {
        key3: 'value3',
        key4: {
            key5: 'value5'
        }
    }
};

const copiedObject = deepCopy(originalObject);
console.log(copiedObject);
```

#### Complete Solution
```javascript
function deepCopy(obj) {
    if (typeof obj !== 'object' || obj === null) {
        return obj;
    }

    const copy = Array.isArray(obj) ? [] : {};

    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            copy[key] = deepCopy(obj[key]);
        }
    }

    return copy;
}

// Example usage
const originalObject = {
    key1: 'value1',
    key2: {
        key3: 'value3',
        key4: {
            key5: 'value5'
        }
    }
};

const copiedObject = deepCopy(originalObject);
console.log(copiedObject);
```

#### Test Cases
```javascript
const originalObject = {
    a: 1,
    b: {
        c: 2,
        d: {
            e: 3
        }
    },
    f: [4, 5, { g: 6 }]
};

const copiedObject = deepCopy(originalObject);
console.log(copiedObject);
// Expected Output: 
// { a: 1, b: { c: 2, d: { e: 3 } }, f: [4, 5, { g: 6 }] }

// Verify deep copy
copiedObject.b.c = 99;
copiedObject.f[2].g = 99;
console.log(originalObject.b.c); // Expected Output: 2
console.log(originalObject.f[2].g); // Expected Output: 6
console.log(copiedObject.b.c); // Expected Output: 99
console.log(copiedObject.f[2].g); // Expected Output: 99
```

These problems provide practical exercises for understanding and working with nested objects, focusing on recursive solutions and deep copying techniques.