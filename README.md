# Web-Scraping-Project-W3Schools-Content-Extractor

This project demonstrates basic web scraping techniques using Python, `requests`, and `BeautifulSoup4` to extract information from the W3Schools website.

## Project Overview

The main goal of this project is to:
1.  Fetch the HTML content of a specified webpage.
2.  Parse the HTML content to make it easily searchable.
3.  Extract the main title of the webpage.
4.  Extract all headings (h1-h6) and their associated paragraphs.
5.  Extract all hyperlinks present on the page.

## Technologies Used

*   **Python**: The core programming language.
*   **`requests`**: A library for making HTTP requests to fetch web pages.
*   **`beautifulsoup4`**: A library for parsing HTML and XML documents.

## Setup and Installation

To run this project, you'll need Python installed. Then, install the necessary libraries using pip:

```bash
pip install requests beautifulsoup4
```

## How to Run

1.  **Clone this repository** (or copy the code into a Colab notebook).
2.  **Execute the Python script/notebook cells** sequentially.

The script will perform the following actions:

*   **Install Dependencies**: Ensures `requests` and `beautifulsoup4` are available.
*   **Fetch Webpage**: Sends an HTTP GET request to `https://www.w3schools.com/`.
*   **Parse HTML**: Uses `BeautifulSoup` to parse the fetched HTML content.
*   **Extract Title**: Prints the main title of the W3Schools homepage.
*   **Extract Headings and Paragraphs**: Identifies all headings and collects paragraphs directly following them.
*   **Extract Links**: Gathers all `<a>` tags' `href` attributes, effectively collecting all links.

## Code Explanation

### `requests` for fetching content

```python
import requests

link = "https://www.w3schools.com/"
page = requests.get(link)
print(page.status_code) # Expected output: 200 for a successful request
```

### `BeautifulSoup` for parsing

```python
from bs4 import BeautifulSoup

my_soup = BeautifulSoup(page.content, "html.parser")
print(my_soup.prettify())
```

### Extracting the main title

```python
title = my_soup.title.string
print(title)
```

### Custom function to extract headings and paragraphs

A function `extract_heading_and_paragraphs(soup)` iterates through all heading tags (`h1` to `h6`). For each heading, it then looks at its subsequent siblings. If a sibling is a paragraph (`<p>` tag) and not another heading, its text content is collected. This provides a structured way to get text content under different sections defined by headings.

### Custom function to extract links

`extract_link(soup)` finds all `<a>` tags in the parsed HTML and retrieves the value of their `href` attribute, effectively collecting all external and internal links on the page.

## Output

The execution of the notebook will output:

*   The HTTP status code (e.g., 200).
*   The prettified HTML content of the page.
*   The main title of the webpage.
*   A structured list of headings and their associated paragraphs.
*   A list of all extracted URLs/links.

Feel free to modify the `link` variable to scrape data from other websites (ensure you respect their `robots.txt` and terms of service).
```
