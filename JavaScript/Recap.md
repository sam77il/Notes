# JavaScript Recap

## Destructuring and Spreading

```js
const products = [
  {
    id: 1,
    name: "Apple",
    description: "This is an apple",
    price: 0.99,
    types: ["a", "b", "c"],
  },
  {
    id: 2,
    name: "Banana",
    description: "This is a banana",
    price: 0.99,
    types: ["a", "b", "c"],
  },
  {
    id: 3,
    name: "Chocolate",
    description: "This is a chocolate",
    price: 1.29,
    types: ["a", "b", "c"],
  },
  {
    id: 4,
    name: "Milk",
    description: "This is milk",
    price: 0.99,
    types: ["a", "b", "c"],
  },
];

function getProductById(id) {
  return products.find((i) => {
    return id === i;
  });
}

const product = getProductById(1);

const { id, name, description, price, types } = product;
id; // 1
name; // Apple
description; // This is an apple
price; // 0.99
types; // ["a", "b", "c"]

const [firstType, ...otherTypes] = types;
firstType; // a
otherTypes; // ["b", "c"]

const newTypes = [...types, "d", "e"];
newTypes;
["a", "b", "c", "d", "e"];

const updatedProduct = { market: "FamilyMart", ...product, price: 2 };
updatedProduct;
//  {
//    id: 1,
//    name: "Apple",
//    description: "This is an apple",
//    price: 2,
//    types: ["a", "b", "c"],
//    market: "FamilyMart"
//  },
```

## Template Literals

```js
const obj = {
  name: "Samil",
  year: 2025,
  date: "21.07.2025",
};

const myString = `His name is ${name} and currently it is the year ${year} or ${
  date.split(".")[2]
}`;

// Note
typeof date.split("."); // object (array)
```

## Ternaries

```js
const isOwned = true;

isOwned ? "He owns that house" : "He does not owns that house";
```

## Arrow Functions

```js
const year = "2000-21-7";

const getYear = (str) => str.split("-")[0];
getYear; // 2000
```

## Falsy Values

- 0
- ""
- null
- undefined
- false

# Short Circuiting

```js
console.log(true && "Some String"); // "Some String"
console.log(false && "Some String"); // false

console.log("samil" && "Some String"); // "Some String"
console.log(0 && "Some String"); // 0

console.log(true || "Some String"); // true
console.log(false || "Some String"); // "Some String"

const spanishTranslation = book.translations.spanish || "NOT TRANSLATED";
spanishTranslation; // NOT TRANSLATED

const reviews = book.reviews.librarything?.reviewsCount ?? "no data";
reviews; // "no data"
```

## Optional Chaining

```js
function getTotalReviewCount(book) {
  const goodreads = book.reviews.goodreads.reviewsCount;
  const librarything = book.reviews.librarything?.reviewsCount ?? 0; // librarything not exists so its undefined
  return goodreads + librarything; // only goodreads
}

console.log(getTotalReviewCount(book)); // 43523
```

## Map Method

```js
const x = [1, 2, 3, 4, 5].map((el) => el * 2);
x; // [ 2, 4, 6, 8, 10]

const books = getBooks(); // Get all books

const titles = books.map((book) => book.title);
titles; // ["blah", "blah2", "blah3", "blah4",]

const essentialData = books.map((book) => {
  return {
    title: book.title,
    author: book.author,
    reviewsCount: getTotalReviewCount(book),
  };
});

essentialData; // [{title: blah blah, author:...}, {title: blah blah, author:...}]
```

## Filter Method

```js
const filteredBooks = books.filter((book) => book.pages > 500);
filteredBooks; // Only Books that has over 500 pages which is stored in an array

const longBooksWithMove = books
  .filter((book) => book.pages > 500)
  .filter((book) => book.hasMovieAdaptation);
longBooksWithMove; // Only books that has over 500 pages and has a movie adaption

const adventureBooks = books
  .filter((book) => book.genres.includes("adventure"))
  .map((book) => book.title);

adventureBooks; // nur die buch titeln welchen die genre adventure haben
```

## Reduce Method

```js
const readingPages = books.reduce((acc, book) => {
  return acc + book.pages; // returns the sum
}, 0);

readingPages; // All Pages added together
```

## Sort Method

```js
const willingToBeSorted = [3, 7, 1, 9, 6];
const sorted = willingToBeSorted.slice().sort((a, b) => a - b); // need slice to make copy to pretend manipulating original array
sorted; // [1, 3, 6, 7, 9]
willingToBeSorted; // [3, 7, 1, 9, 6]

const sortedByPages = books
  .slice()
  .sort((a, b) => b.pages - a.pages)
  .map((book) => ({ title: book.title, pages: book.pages }));
sortedByPages; // sorted array with objects with key and values
```

## Add Item in Array

```js
const booksAfterAdd = [
  ...books,
  { id: books.length + 1, title: "Test", author: "King" },
];
console.log(booksAfterAdd.length);
```

## Delete Item in Array

```js
const booksAfterDelete = booksAfterAdd.filter((book) => book.id !== 3);
console.log(booksAfterDelete.length);
```

## Edit Item in Array

```js
const booksAfterEdit = booksAfterDelete.map((book) =>
  book.id === 1 ? { ...book, title: "Amadeus" } : book
);
console.log(booksAfterEdit[4]);
```

## Using Promises

```js
fetch("https://jsonplaceholder.typicode.com/todos")
  .then((res) => res.json())
  .then((data) => console.log(data));
```

## Using Async Await

```js
async function getTodos() {
  const res = await fetch("https://jsonplaceholder.typicode.com/todos");
  const data = await res.json();
  console.log(data);
}

getTodos();
```
