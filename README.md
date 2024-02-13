# Women's Organizations Data Scraping and Cleaning

## Overview

This Python script scrapes data from the Wikipedia page listing women's organizations and saves the extracted content to a CSV file. The script utilizes the BeautifulSoup library to parse HTML content and extract relevant information, which is then cleaned using custom text cleaning functions.

## Requirements

To run this script, you need the following Python libraries installed:

- BeautifulSoup (`bs4`): For parsing HTML content and extracting data from web pages.
- Requests (`requests`): Enables making HTTP requests to fetch the HTML content of web pages.
- Pandas (`pandas`): Essential for data manipulation and handling tabular data structures.
- CSV (`csv`): Necessary for reading from and writing to CSV files.
- Regular Expressions (`re`): Provides support for pattern matching and text manipulation.

You can install these dependencies via pip:

```bash
pip install beautifulsoup4 requests pandas
```

## Usage

1. **Run the Script**:
   - Execute the Python script (`women_org_scraper.py`) to scrape data from the Wikipedia page and save it to a CSV file:

   ```bash
   python women_org_scraper.py
   ```

   This will generate a CSV file named `Women_Org.csv` in the specified directory (`D:\DA\Python\For Optevus\`).

2. **Customization**:
   - **URL**: Modify the `url` variable in the script to target a different Wikipedia page if needed. Ensure that the page structure and content are compatible with the scraping logic.
   - **Output File**: Change the output CSV file path and name by modifying the `csvfile` variable in the script.

3. **Text Cleaning Function** (`clean_text()`):
   - The `clean_text()` function defines a set of operations to clean the extracted text:
     - It employs regular expressions (regex) to remove numbers and special characters from the text, except spaces and common punctuation marks.
     - The regex pattern `[a-zA-Z\s,!?]` matches any alphabetic character (`a-z` and `A-Z`), whitespace (`\s`), and common punctuation marks (`,` and `!?`), effectively removing all other characters from the text.
     - Additionally, it uses string manipulation methods (`split(',')` and `split('.')`) to extract content before the first comma and remove content after the first full stop.
     - The cleaned text is then stripped of leading and trailing whitespace.

4. **Usage of Regular Expressions (Regex)**:
   - Regular expressions (regex) are a powerful tool for pattern matching and text manipulation in Python.
   - In the provided code, the regex pattern `[a-zA-Z\s,!?]` is used to match and retain only alphabetic characters (both lowercase and uppercase), whitespace, commas, and common punctuation marks (`!` and `?`).
   - Any characters outside this pattern, such as numbers and special characters, are replaced with an empty string, effectively removing them from the text.
   - Regular expressions provide flexibility and precision in defining text patterns, making them invaluable for tasks like text cleaning and data extraction in web scraping projects.


5. **Fetching HTML Content**:
   - The script specifies the URL of the Wikipedia page (`url`) from which data will be scraped.
   - It uses the `requests.get()` function to fetch the HTML content of the specified URL.
   - The HTML content is then parsed using BeautifulSoup (`BeautifulSoup(page.text, 'html.parser')`) to create a BeautifulSoup object (`soup`).

6. **Locating Relevant HTML Element**:
   - The script searches for a specific `<div>` element within the parsed HTML content.
   - The desired content, i.e., the list of women's organizations, is expected to be contained within this `<div>` element.

7. **Scraping and Writing to CSV**:
   - The script opens a CSV file (`Women_Org.csv`) in write mode, ready to store the extracted data.
   - It creates a `csv.writer` object (`writer`) to facilitate writing data to the CSV file.
   - The script iterates over each unordered list (`<ul>`) within the identified `<div>` element.
   - For each list item (`<li>`) within the unordered list, it extracts the text content and cleans it using the `clean_text()` function.
   - The cleaned content is then written to the CSV file using the `writer.writerow()` function.

8. **Conclusion**:
   - Once the script has completed execution, the extracted data will be saved in the specified CSV file (`Women_Org.csv`), ready for further analysis or processing.

Overall, this script demonstrates the process of scraping data from a web page, cleaning the extracted text, and saving it to a CSV file using Python libraries such as BeautifulSoup and pandas. It provides a practical example of web scraping and data preprocessing techniques.

