BeautifulSoup Webscraping

BeautifulSoup is a Python library used in web scraping to parse and extract data from HTML or XML web pages. 

It converts the webpage’s source code into a structured format (a parse tree), making it easy to locate and retrieve specific elements such as headings, links, tables, or text. 

BeautifulSoup is commonly used together with Requests to download web pages and then extract useful information from them efficiently.

Import Requests, which is used to send HTTP requests to websites and retrieve webpage content.

Import Pandas and gives it the alias pd, which is commonly used to store, organize, and analyze scraped data in tables (DataFrames).

Import BeautifulSoup, which is used to parse the HTML of a webpage and extract specific elements like titles, links, or text.

Then place the URL for parsing the respective link.

headers
Creates a dictionary called headers that will be sent along with an HTTP request to a website.

"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
This header tells the website that the request is coming from a real web browser on Windows, which helps avoid being blocked during web scraping.

"Accept-Language": "en-US,en;q=0.9"
This header tells the server that the preferred language for the webpage response is English (US). where q=0.9 is the quality factor where the language is 90% preference in english.

response = requests.get(url, headers=headers)

This line uses Requests to send an HTTP GET request to the specified url with custom headers and store the server’s response in the variable response.

soup = BeautifulSoup(response.text, "html.parser")

Creates a BeautifulSoup object from the webpage’s HTML content (response.text) using the HTML parser, so the page structure can be easily searched and extracted.

movies = soup.find_all("li", class_="ipc-metadata-list-summary-item")

Finds all list elements with the class ipc-metadata-list-summary-item in the HTML page and stores them in the list movies.

print(f"Movie Count :{len(movies)}")

The movies are displayed only 25 because it scarpe the list of movies in the imdb website where the page contains only 25 movies in a single page.

Prints the total number of movie elements found by calculating the length of the movies list.

Then the loop goes through each movie element, extracts the title, rank, year, and rating, and stores them as dictionaries inside the list data.

Pandas converts the list data into a DataFrame (df) and df.head() prints the first few rows of the scraped movie data.

Saves the dataframe into the csv file .

