

# Image Search App

This is a simple Image Search App that allows you to search for images using the Unsplash API.

---

## Table of Contents

* [Features](#features)
* [Technologies Used](#technologies-used)
* [Getting Started](#getting-started)
    * [Prerequisites](#prerequisites)
    * [Cloning the Repository](#cloning-the-repository)
    * [Opening in VS Code](#opening-in-vs-code)
    * [Running the Application](#running-the-application)
* [Code Explanation](#code-explanation)
    * [HTML Structure (`index.html`)](#html-structure-indexhtml)
    * [CSS Styling (`style.css`)](#css-styling-stylecss)
    * [JavaScript Functionality (`script.js`)](#javascript-functionality-scriptjs)
* [License](#license)
* [Author](#author)

---

## Features

* Search for images by keyword.
* Display search results in a responsive grid.
* "Show More" button to load additional images.
* Links to the original image on Unsplash.

---

## Technologies Used

* **HTML5**: For the basic structure of the web page.
* **CSS3**: For styling the application and making it visually appealing.
* **JavaScript (ES6+)**: For handling user interaction, fetching data from the Unsplash API, and dynamically updating the content.
* **Unsplash API**: To fetch image data.

---

## Getting Started

Follow these instructions to get a copy of the project up and running on your local machine.

### Prerequisites

You'll need the following installed on your computer:

* **Git**: For cloning the repository.
* **A modern web browser**: Such as Chrome, Firefox, Safari, or Edge.
* **VS Code (or any other code editor)**: For viewing and editing the code.

### Cloning the Repository

1.  **Open your Terminal or Command Prompt.** You can usually find this by searching for "Terminal" on macOS/Linux or "Command Prompt" on Windows.
2.  **Navigate to the directory** where you want to store the project. For example, if you want to put it in a `Projects` folder within your `Documents`, you'd type:
    ```bash
    cd Documents/Projects
    ```
    If the folder doesn't exist, you can create it first: `mkdir Documents/Projects`.
3.  **Clone the repository** using the following command:
    ```bash
    git clone <repository-url>
    ```
    *(Replace `<repository-url>` with the actual URL of this repository. If you're viewing this README in the cloned repository, you already have it!)*

### Opening in VS Code

1.  **Open VS Code.**
2.  Go to **File > Open Folder...** (or `Cmd+K Cmd+O` on macOS, `Ctrl+K Ctrl+O` on Windows/Linux).
3.  **Navigate to the cloned repository folder** (e.g., `Image-Search-App`) and click **Open**.

### Running the Application

This is a front-end application, so you don't need a server to run it.

1.  **Locate the `index.html` file** in the project folder within VS Code's file explorer (usually on the left sidebar).
2.  **Right-click on `index.html`** and select **"Open with Live Server"** if you have the Live Server extension installed in VS Code. This is the recommended way as it automatically reloads your browser when you make changes.
3.  Alternatively, you can **drag the `index.html` file directly into your web browser** to open it.

---

## Code Explanation

Let's break down how the different files contribute to the Image Search App.

### HTML Structure (`index.html`)

This file provides the basic layout and content of the web page.

* `<!DOCTYPE html>`: Declares the document type.
* `<html lang="en">`: The root element, specifying the language as English.
* `<head>`: Contains metadata about the page.
    * `<meta charset="UTF-8">`: Specifies the character encoding.
    * `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Configures the viewport for responsive design, making the app look good on different devices.
    * `<title>Image Search App</title>`: Sets the title that appears in your browser tab.
    * `<link rel="stylesheet" href="style.css">`: Links to the external CSS file, which handles all the styling.
* `<body>`: Contains the visible content of the web page.
    * `<h1>Image Search App</h1>`: The main heading for your application.
    * `<form action="">`: A form for user input.
        * `<input type="text" id="search-input" placeholder="Search for images">`: This is where users type what they want to search for.
        * `<button id="search-button" type="submit">Search</button>`: The button users click to start the search.
    * `<div class="search-results">`: This container is where the fetched image results will be displayed. It includes some initial placeholder images for demonstration purposes.
        * Each `div` with class `search-result` represents an individual image display, containing an `<img>` tag and an `<a>` tag that links to the original image.
    * `<button id="show-more-btn">Show more</button>`: This button will appear after the first search to load more images (it's initially hidden).
    * `<script src="script.js"></script>`: Links to the external JavaScript file. It's placed at the end of the `<body>` so that the HTML elements are fully loaded before the script tries to interact with them.

### CSS Styling (`style.css`)

This file defines the visual presentation of the application, making it look good.

* `@import url(...)`: Imports the "Poppins" font from Google Fonts, giving the app a modern and clean typeface.
* `* { ... }`: A **universal selector** that applies basic resets to all elements, removing default margins/paddings and setting `box-sizing` for consistent layout.
* `body { ... }`: Sets basic line height for the entire body.
* `h1 { ... }`: Styles the main heading, centering it and adjusting font size and weight.
* `form { ... }`: Styles the search form, using **flexbox** to easily center its content horizontally.
* `#search-input { ... }`: Styles the input field, including its width, padding, border, shadow, and font size.
* `#search-button { ... }`: Styles the search button with a background color, text color, padding, and a pointer cursor when hovered.
* `.search-results { ... }`: This is a crucial part for the layout. It uses **CSS `columns`** to create a responsive grid layout for the images, adapting nicely to different screen sizes. `column-gap` adds space between columns.
* `.search-result { ... }`: Styles individual image containers, adding a subtle shadow, rounded corners (`border-radius`), and handling overflow. `break-inside: avoid;` is important here to prevent images from being cut off if they span across columns.
* `.search-result img { ... }`: Styles the images within the results, ensuring they fill their container, maintain their aspect ratio (`object-fit: cover;`), and have a smooth opacity transition on hover for a nice visual effect.
* `.search-result a { ... }`: Styles the link below each image, providing basic text styling and padding, and making the text capitalize.
* `#show-more-btn { ... }`: Styles the "Show more" button, centering it and initially hiding it (`display: none;`) until search results are displayed.
* `@media screen and (max-width: ...)`: These **media queries** are key for responsiveness. They adjust the number of columns in the `.search-results` grid for smaller screens (e.g., 2 columns for tablets, and 1 column for mobile phones), ensuring a good user experience on all devices.

### JavaScript Functionality (`script.js`)

This file contains the logic that makes the application interactive, fetches data from the Unsplash API, and dynamically updates the content.

* `const accesskey = "Me7-q9Vwj5QtkLTMbTYj0htk8KR6JtLYdQafMnsTY1s"`: This line defines your **Unsplash API access key**. **Important Note:** For a real-world, production application, it's generally recommended to handle API keys more securely (e.g., using environment variables or a backend server) rather than directly exposing them in client-side code like this.
* `const formEl = document.querySelector("form")`: Selects the entire form element.
* `const inputEl = document.getElementById("search-input")`: Selects the input field where users type their search query.
* `const searchResults = document.querySelector(".search-results")`: Selects the `div` where all the image results will be displayed.
* `const showMore = document.getElementById("show-more-btn")`: Selects the "Show more" button.
* `let inputData = ""`: A variable to store the current search query entered by the user.
* `let page = 1;`: A variable to keep track of the current page of search results for pagination (loading more images).
* `async function searchImages() { ... }`: This is the core asynchronous function that handles fetching images from Unsplash.
    * `inputData = inputEl.value;`: Gets the current text typed into the search input.
    * `const url = \`https://api.unsplash.com/search/photos?page=${page}&query=${inputData}&client_id=${accesskey}\`;`: Constructs the Unsplash API URL, including the current page number (`${page}`), the user's search query (`${inputData}`), and your `client_id` (access key).
    * `const response = await fetch(url);`: Makes an asynchronous network request to the Unsplash API. The `await` keyword pauses the function until the response is received.
    * `const data = await response.json();`: Parses the JSON data received from the API response into a JavaScript object.
    * `const results = data.results;`: Extracts the actual array of image results from the parsed data.
    * `if( page === 1 ){ searchResults.innerHTML = ""; }`: If it's the very first page of results (meaning a new search), it clears any previously displayed images to make room for new ones.
    * `results.map((result) => { ... })`: This loop iterates over each image `result` obtained from the API. For each result:
        * `const imageWrapper = document.createElement("div");`: Creates a new `div` element to hold the image and its link.
        * `imageWrapper.classList.add("search-result");`: Adds the `search-result` CSS class for styling.
        * `const image = document.createElement("img");`: Creates an `<img>` element.
        * `image.src = result.urls.small;`: Sets the source of the `<img>` to a small version of the image provided by Unsplash.
        * `image.alt = result.alt_description;`: Sets the `alt` text for accessibility purposes.
        * `const imageLink = document.createElement("a");`: Creates an `<a>` (anchor) element for the link.
        * `imageLink.href = result.links.html;`: Sets the link's destination to the original image page on Unsplash.
        * `imageLink.target = "_blank" ;`: Makes the link open in a new browser tab.
        * `imageLink.textContent = result.alt_description;`: Sets the visible text of the link to the image's description.
        * `imageWrapper.appendChild(image); imageWrapper.appendChild(imageLink);`: Adds the `<img>` and `<a>` elements as children to the `imageWrapper`.
        * `searchResults.appendChild(imageWrapper);`: Appends the complete `imageWrapper` (containing the image and link) to the `search-results` container on the webpage, making it visible.
    * `page++`: Increments the `page` number so that the next time `searchImages` is called, it fetches the next set of results.
    * `if(page > 1){ showMore.style.display= "block" }`: If we've fetched at least one set of results (i.e., `page` is now greater than 1), the "Show more" button is made visible.
* `formEl.addEventListener("submit", (event) => { ... });`: Adds an **event listener** to the form. This code runs whenever the form is submitted (e.g., by pressing Enter in the input field or clicking the Search button).
    * `event.preventDefault()`: This is crucial! It stops the browser from performing its default action for a form submission, which would normally cause the page to reload.
    * `page = 1;`: Resets the page number to 1 because it's a new search query.
    * `searchImages();`: Calls the `searchImages` function to fetch and display the new results.
* `showMore.addEventListener("click", () => { searchImages(); });`: Adds an **event listener** to the "Show more" button. When this button is clicked, it simply calls `searchImages()` again, which will fetch the *next* page of results due to the `page++` logic.

---

---

## Author

* **Ahmed Mohamed**

---
