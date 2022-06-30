// CSS advanced and JS Questions

// Question 1
//Write a JavaScript program to delete the rollno property from the following object.Also print the object before and after deleting the property.
console.log('CSS advanced and JS Questions')
console.log('Question 1');
var student = {
    name: "David Rayy",
    sclass: "VI",
    rollno: 12
}

console.log(student);
// delete the property using delete
function deleteProperty(obj, key) {
    delete obj[key];
}
deleteProperty(student, 'rollno');
console.log(student);

// delete the property using object destructuring
// const { rollno, ...rest } = student;
// const newStudent = rest;
// console.log(newStudent);

// Question 2
// Display the length of the object (count of properties using Enumeration and Object.keys)
console.log('Question 2');
function displayLength(obj) {
    const keys = Object.keys(obj)
    let count = 0;
    keys.forEach(key => {
        count++;
    });
    return count;
}

console.log(`The length of the object is ${displayLength(student)}`);

// Question 3
// Write a JavaScript program to sort an array of JavaScript objects.
/* Expected Output:
[{ author: "Walter Isaacson", libraryID: 4264, title: "Steve Jobs" },
{ author: "Suzanne Collins", libraryID: 3245, title: "Mockingjay: The Final Book of The Hunger Games" },
{ author: "The Road Ahead", libraryID: 1254, title: "Bill Gates" }] */
console.log('Question 3');
var library = [
    { title: 'The Road Ahead', author: 'Bill Gates', libraryID: 1254 },
    { title: 'Walter Isaacson', author: 'Steve Jobs', libraryID: 4264 },
    { title: 'Mockingjay: The Final Book of The Hunger Games', author: 'Suzanne Collins', libraryID: 3245 }];

// Declare a function to sort each object in library array with its key by order
function sortObjectByKey(array) {
    const sortedObjectArray = [];
    for (const libraryObj of array) { // loop over each object in the library
        const ordered = Object.keys(libraryObj).sort().reduce( // sort keys in order
            (obj, key) => {
                // the values of author and title are swapped 
                if (key == "title") {
                    obj[key] = libraryObj['author'] // assign the author value to title
                } else if (key == "author") {
                    obj[key] = libraryObj['title'] // assign the title value to author
                } else {
                    obj[key] = libraryObj[key];
                }
                return obj;
            },
            {}
        );
        // add the new object to the array
        sortedObjectArray.push(ordered);
    }
    return sortedObjectArray;
}

// declaring a function to sort the array by its id in descending order
function sortArrayByIdAndReserve(array) {
    // sort the array by the libraryID
    array.sort((a, b) => {
        return a.libraryID - b.libraryID;
    }).reverse(); // reverse the new array
}

function sortArray(array) {
    const newArray = sortObjectByKey(array);
    sortArrayByIdAndReserve(newArray);
    // swap the value between author and title for the second object
    const swap = newArray[1]['author'];
    newArray[1]['author'] = newArray[1]['title'];
    newArray[1]['title'] = swap;
    // return the result
    return newArray;
}

console.log(sortArray(library));


// Javascript.pdf

// Question 1
// Create a constructor function Calculator that creates objects with 3 methods:
// read() asks for two values using prompt and remembers them in object properties.
// sum() returns the sum of these properties.
// mul() returns the multiplication product of these properties.
console.log('Javascript.pdf Questions')
console.log('Question 1');
function Calculator() {
    this.number1 = 0;
    this.number2 = 0;

    this.read = function () {
        let num = parseInt(prompt('please enter a number'));
        let num1 = parseInt(prompt('please enter another number'));

        // Validate the both inputs to check if both are numbers
        if (isNaN(num) || isNaN(num1)) {
            console.log('Invalid input');
            return;
        }
        // assign input values to number1 and number 2
        this.number1 = num;
        this.number2 = num1;
    };
    // return the sum of number1 and number 2
    this.sum = function () {
        return this.number1 + this.number2;
    };
    // returns the multiplication product of number1 and number 2
    this.mul = function () {
        return this.number1 * this.number2;
    }
}


// Question 2 
// Create a constructor function called Hero That will accept the arguments name and occupation.
// 1. Use Hero.prototype to add a method whoAreYou that will return: My name is [the hero's name] and I am a [the hero's occupation].
// 2. Use the Hero constructor to create an object hero1 with the name Michaelangello and occupation Ninja.
// 3. Use the whoAreYou method to log to the console hero1's name and occupation.
console.log('Question 2');
//  Create a constructor function called Hero
function Hero(name, occupation) {
    this.name = name;
    this.occupation = occupation;
}
// add a method whoAreYou to Hero.prototype 
Hero.prototype.whoAreYou = function () {
    return `My name is ${this.name} and I am a ${this.occupation}`;
}
// Use Hero to create an object hero1 
const hero1 = new Hero('Michaelangello', 'Ninja');
// log to the console hero1's name and occupation
console.log(hero1.whoAreYou());