#Problem - 1
function calculateTotal(numbers) {
  let total = 0;

  for (let i = 0; i <= numbers.length; i++) {
    total += numbers[i];
  }

  return total;
}

console.log(calculateTotal([10, 20, 30]));

#Issues Identify:- 
- The loop condition should be "i < numbers.length" instead of "i <= numbers.length" to avoid an out-of-bounds error.
- The function does not handle the case where the input array is empty.

#Debug and fix version of code:

function calculateTotal(numbers) {
  let total = 0;

  for (let i = 0; i < numbers.length; i++) {
    total += numbers[i];
  }

  return total;
}

console.log(calculateTotal([10, 20, 30]));

#Problem - 2

function removeDuplicates(numbers) {
  const result = [];

  numbers.forEach((number) => {
    if (result.indexOf(number)) {
      result.push(number);
    }
  });

  return result;
}

console.log(removeDuplicates([1, 2, 2, 3, 1, 4]));

#Issues Identify:-
- The condition in the if statement should check if the index is equal to -1 (not found) instead of just checking if it exists, which will always be true for non-zero indices.

#Debug and fix version of code:
function removeDuplicates(numbers) {
  const result = [];

  numbers.forEach((number) => {
    if (result.indexOf(number) === -1) {
      result.push(number);
    }
  });

  return result;
}

console.log(removeDuplicates([1, 2, 2, 3, 1, 4]));

Problem - 3
function sortScores(scores) {
  return scores.sort();
}

console.log(sortScores([80, 9, 100, 25, 3]));

#Issues Identify:-
- The sort method sorts elements as strings by default, which can lead to incorrect ordering for numbers.

#Debug and fix version of code:
function sortScores(scores) {
    return scores.sort((a, b) => a - b);
    }
console.log(sortScores([80, 9, 100, 25, 3]));


Problem - 4
const products = [
  { id: 1, name: "Laptop", price: 50000 },
  { id: 2, name: "Mouse", price: 500 }
];

function getProduct(id) {
  return products.find((product) => product.id === id);
}

console.log(getProduct("2").name);

#Issues Identify:-
- The function getProduct expects a number for the id, but the console.log is passing a string. This will cause the find method to return undefined.

#Debug and fix version of code:
const products = [
  { id: 1, name: "Laptop", price: 50000 },
  { id: 2, name: "Mouse", price: 500 }
];

function getProduct(id) {
  return products.find((product) => product.id === id);
}

console.log(getProduct(2).name);

Problem - 5
function countOccurrences(numbers, target) {
  let count = 0;

  numbers.forEach((number) => {
    if (number = target) {
      count++;
    }
  });

  return count;
}

console.log(countOccurrences([1, 2, 2, 3, 2], 2));

#Issues Identify:-
- The condition in the if statement uses a single equals sign = which is an assignment operator
, instead of a double equals sign == or triple equals sign === for comparison.

#Debug and fix version of code:
function countOccurrences(numbers, target) {
  let count = 0;

  numbers.forEach((number) => {
    if (number === target) {
      count++;
    }
  });

  return count;
}

console.log(countOccurrences([1, 2, 2, 3, 2], 2));

Problem - 6
const cart = [
  { name: "Keyboard", price: 1000, quantity: 2 },
  { name: "Mouse", price: 500, quantity: 1 }
];

function calculateCartTotal(items) {
  return items.reduce((total, item) => {
    total + item.price * item.quantity;
  }, 0);
}

console.log(calculateCartTotal(cart));

#Issues Identify:-
- The reduce callback function does not return the updated total, which will result in undefined being returned.

#Debug and fix version of code:
const cart = [
  { name: "Keyboard", price: 1000, quantity: 2 },
  { name: "Mouse", price: 500, quantity: 1 }
];

function calculateCartTotal(items) {
  return items.reduce((total, item) => {
    return total + item.price * item.quantity;
  }, 0);
}

console.log(calculateCartTotal(cart));

Problem - 7
function getAdults(users) {
  return users.filter((user) => {
    user.age >= 18;
  });
}

console.log(
  getAdults([
    { name: "A", age: 17 },
    { name: "B", age: 22 },
    { name: "C", age: 19 }
  ])
);

#Issues Identify:-
- The filter callback function does not return a value, which will result in an empty array being returned.

#Debug and fix version of code:
function getAdults(users) {
  return users.filter((user) => {
   return user.age >= 18;
  });
}

console.log(
  getAdults([
    { name: "A", age: 17 },
    { name: "B", age: 22 },
    { name: "C", age: 19 }
  ])
);

Problem - 8
function getUser() {
  return new Promise((resolve) => {
    setTimeout(() => {
     return resolve({ id: 1, name: "Avinash" });
    }, 1000);
  });
}

function displayUser() {
  const user = getUser();
  console.log(user.name);
}

displayUser();

#Issues Identify:-
- The getUser function returns a Promise, so the displayUser function needs to handle the asynchronous
    nature of the Promise using async/await or .then()

#Debug and fix version of code:
function getUser() {
  return new Promise((resolve) => {
    setTimeout(() => {
     return resolve({ id: 1, name: "Avinash" });
    }, 1000);
  });
}

async function displayUser() {
  const user =await getUser();
  console.log(user.name);
}

displayUser();

Problem - 9
async function fetchProducts() {
  try {
    const response = await fetch("/api/products");
    const products = await response.json();
    return products
  } catch (error) {
    console.log("Failed to load products");
  }
}

fetchProducts().then((products) => {
  console.log(products.length);
});

#Issues Identify:-
- The fetchProducts function does not return anything in the catch block, which will result in undefined being returned if an error occurs. This can cause issues when trying to access properties of the returned value.

#Debug and fix version of code:
async function fetchProducts() {
  try {
    const response = await fetch("/api/products");
    const products = await response.json();
    return products;
  } catch (error) {
    console.log("Failed to load products");
    return [];
  }
}
fetchProducts().then((products) => {
  console.log(products.length);
});

Problem - 10
function calculateDiscount(price) {
  if (price > 1000) {
    let discount = price * 0.1;
  }

  return discount;
}

console.log(calculateDiscount(2000));

#Issues Identify:-
- The variable discount is declared inside the if block, so it is not accessible outside of that block. This will result in a ReferenceError when trying to return discount.

#Debug and fix version of code:
function calculateDiscount(price) {
  let discount = 0;
  if (price > 1000) {
    discount = price * 0.1;
  }
  return discount;
}

console.log(calculateDiscount(2000));

Problem - 11
const user = {
  name: "Avinash",
  address: {
    city: "Davangere"
  }
};

function updateUser(currentUser) {
  const updatedUser = { ...currentUser };
  updatedUser.address.city = "Bengaluru";

  return updatedUser;
}

const newUser = updateUser(user);

console.log(user.address.city);
console.log(newUser.address.city);

#Issues Identify:-
- The updateUser function creates a shallow copy of the currentUser object, which means that the address property is still a reference to the same object. Modifying updatedUser.address.city will also modify user.address.city.

#Debug and fix version of code:
const user = {
  name: "Avinash",
  address: {
    city: "Davangere"
  }
};

function updateUser(currentUser) {
  const updatedUser = { ...currentUser };
  updatedUser.address = { ...currentUser.address };
  updatedUser.address.city = "Bengaluru";

  return updatedUser;
}

const newUser = updateUser(user);

console.log(user.address.city);
console.log(newUser.address.city);

Problem - 12
function searchProducts(products, query) {
  return products.filter((product) =>
    product.name.toLowerCase().includes(query)
  );
}

const products = [
  { name: "Laptop" },
  { name: "Mouse" },
  { name: "Keyboard" }
];

console.log(searchProducts(products, "LAP"));

#Issues Identify:-
- The query string should also be converted to lowercase to ensure a case-insensitive search.

#Debug and fix version of code:
function searchProducts(products, query) {
  const lowerCaseQuery = query.toLowerCase();
  return products.filter((product) =>
    product.name.toLowerCase().includes(lowerCaseQuery)
  );
}

const products = [
  { name: "Laptop" },
  { name: "Mouse" },
  { name: "Keyboard" }
];

console.log(searchProducts(products, "LAP"));

Problem - 13
function debounce(callback, delay) {
  let timer;

  return function (...args) {
    setTimeout(() => {
      callback(...args);
    }, delay);
  };
}

const logSearch = debounce((value) => {
  console.log(value);
}, 500);

logSearch("R");
logSearch("Re");
logSearch("React");

#Issues Identify:-
- The debounce function does not clear the previous timer, which means that all the calls to logSearch will execute after the delay, instead of only the last one.

#Debug and fix version of code:
function debounce(callback, delay) {
  let timer;

  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => {
      callback(...args);
    }, delay);
  };
}

const logSearch = debounce((value) => {
  console.log(value);
}, 500);

logSearch("R");
logSearch("Re");
logSearch("React");

Problem - 14
function groupByCategory(products) {
  const result = {};

  products.forEach((product) => {
    result[product.category] = result[product.category] || [];
    result[product.category].push(product);
  });

  return result;
}

const products = [
  { name: "Laptop", category: "Electronics" },
  { name: "Phone", category: "Electronics" },
  { name: "Chair", category: "Furniture" }
];

console.log(groupByCategory(products));
console.log(groupByCategory(products));

#Issues Identify:-
- The function works correctly, but it can be improved for readability and performance by using the reduce method instead of forEach.

#Debug and fix version of code:
function groupByCategory(products) {
  return products.reduce((result, product) => {
    (result[product.category] = result[product.category] || []).push(product);
    return result;
  }, {});
}

Problem - 15
function paginate(items, page, pageSize) {
  const startIndex = page * pageSize;

  return items.slice(startIndex, startIndex + pageSize);
}

const items = ["A", "B", "C", "D", "E"];

console.log(paginate(items, 1, 2));
console.log(paginate(items, 2, 2));

#Issues Identify:-
- The page parameter should be zero-based, but the function currently treats it as one-based.

#Debug and fix version of code:
function paginate(items, page, pageSize) {
  const startIndex = (page - 1) * pageSize;

  return items.slice(startIndex, startIndex + pageSize);
}
const items = ["A", "B", "C", "D", "E"];
console.log(paginate(items, 1, 2));
console.log(paginate(items, 2, 2));

Problem - 16
function wait(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

async function processItems(items) {
  items.forEach(async (item) => {
    await wait(100);
    console.log(item);
  });

  console.log("Processing complete");
}

processItems([1, 2, 3]);

#Issues Identify:-
- The forEach loop does not wait for the async operations to complete, so "Processing complete" will be logged before all items are processed. This can be fixed by using a for...of loop or Promise.all

#Debug and fix version of code:
function wait(ms) {
    return new Promise((resolve) => setTimeout(resolve, ms));
    }
async function processItems(items) {
    for (const item of items) {
        await wait(100);
        console.log(item);
    }
    console.log("Processing complete");
}
processItems([1, 2, 3]);

Problem -17
function validateForm(form) {
  if (!form.name && form.email && form.password.length >= 8) {
    return true;
  }

  return false;
}

console.log(
  validateForm({
    name: "Avinash",
    email: "avinash@example.com",
    password: "password123"
  })
);

#Issues Identify:-
- The condition in the if statement is incorrect. It should check if all fields are valid, but currently it checks if name is falsy and email is truthy and password length is greater than or equal to 8. This will return false for valid forms.

#Debug and fix version of code:
function validateForm(form) {
  if (form.name && form.email && form.password.length >= 8) {
    return true;
  }

  return false;
}

console.log(
  validateForm({
    name: "Avinash",
    email: "avinash@example.com",
    password: "password123"
  })
);

Problem - 18
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  function increment() {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
  }

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default Counter;

#Issues Identify:-
- The increment function calls setCount multiple times with the same value of count, which will not result in the expected increment. Instead, it should use the functional form of setCount to ensure that each update is based on the previous state.

#Debug and fix version of code:
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  function increment() {
    setCount(prev=> prev + 1);
    setCount(prev=>prev+1);
    setCount(prev=>prev + 1);
  }

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default Counter;

Problem - 19
import { useEffect, useState } from "react";

type Product = {
  id: number;
  name: string;
  price: number;
};

function ProductList() {
  const [products, setProducts] = useState<Product[]>([]);

  useEffect(() => {
    fetch("/api/products")
      .then((response) => response.json())
      .then((data) => setProducts(data));
  }, []);

  return (
    <div>
      {products.map((product) => (
        <div>
          <h3>{product.name}</h3>
          <p>₹{product.price}</p>
          <button onClick={() => console.log(product.id)}>
            View
          </button>
        </div>
      ))}
    </div>
  );
}

export default ProductList;

#Issues Identify:-
- The map function should include a unique key prop for each child element to help React identify which items have changed, are added, or are removed. This can be fixed by adding a key prop to the outer div in the map function.

#Debug and fix version of code:
import { useEffect, useState } from "react";

type Product = {
  id: number;
  name: string;
  price: number;
};

function ProductList() {
  const [products, setProducts] = useState<Product[]>([]);

  useEffect(() => {
    fetch("/api/products")
      .then((response) => response.json())
      .then((data) => setProducts(data));
  }, []);

  return (
    <div>
      {products.map((product) => (
        <div key={product.id}>
          <h3>{product.name}</h3>
          <p>₹{product.price}</p>
          <button onClick={() => console.log(product.id)}>
            View
          </button>
        </div>
      ))}
    </div>
  );
}

export default ProductList;

Problem - 20
import { useState } from "react";

function ProductSearch() {
  const [search, setSearch] = useState("");
  const [products] = useState([
    "Laptop",
    "Mouse",
    "Keyboard",
    "Monitor"
  ]);

  const filteredProducts = products.filter((product) =>
    product.toLowerCase().includes(search)
  );

  return (
    <div>
      <input
        value={search}
        onChange={(event) => setSearch(event.target.value)}
        placeholder="Search products"
      />

      {filteredProducts.length === 0 && (
        <p>No products found</p>
      )}

      {filteredProducts.map((product) => (
        <p>{product}</p>
      ))}
    </div>
  );
}

export default ProductSearch;

#Issues Identify:-
- The search string should be converted to lowercase to ensure a case-insensitive search. This can
    be fixed by converting the search string to lowercase in the filter method.
-map function should include a unique key prop for each child element to help React identify which items have changed, are added, or are removed. This can be fixed by adding a key prop to the p element in the map function.

#Debug and fix version of code:
import { useState } from "react";
function ProductSearch() {
  const [search, setSearch] = useState("");
  const [products] = useState([
    "Laptop",
    "Mouse",
    "Keyboard",
    "Monitor"
  ]);

  const filteredProducts = products.filter((product) =>
    product.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div>
      <input
        value={search}
        onChange={(event) => setSearch(event.target.value)}
        placeholder="Search products"
      />

      {filteredProducts.length === 0 && (
        <p>No products found</p>
      )}

      {filteredProducts.map((product, index) => (
        <p key={index}>{product}</p>
      ))}
    </div>
  );
}
