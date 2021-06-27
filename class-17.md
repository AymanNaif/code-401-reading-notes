# How to Web Scrape with Python in 4 Minutes

**Web Scraping**

Web scraping is a technique to automatically access and extract large amounts of information from a website, which can save a huge amount of time and effort. 

**Important notes about web scraping:**
- Read through the website’s Terms and Conditions to understand how you can legally use the data. Most sites prohibit you from using the data for commercial purposes.
- Make sure you are not downloading data at too rapid a rate because this may break the website. You may potentially be blocked from the site as well.

**Inspecting the Website**

The first thing that we need to do is to figure out where we can locate the links to the files we want to download inside the multiple levels of HTML tags. Simply put, there is a lot of code on a website page and we want to find the relevant pieces of code that contains our data.

**Python Code**

We start by importing the following libraries.
```
import requests
import urllib.request
import time
from bs4 import BeautifulSoup
```
Next, we set the url to the website and access the site with our requests library.
```
url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
```
[Web Scrape with Python](https://towardsdatascience.com/how-to-web-scrape-with-python-in-4-minutes-bc49186a8460)

# Web scraping

Web scraping, web harvesting, or web data extraction is data scraping used for **extracting data from websites**. 

Web scraping software may access the World Wide Web directly using the **Hypertext Transfer Protocol**, or through a **web browser**. While web scraping can be done manually by a software user, the term typically refers to automated processes implemented using a bot or web crawler. It is a form of copying, in which specific data is gathered and copied from the web, typically into a central local database or spreadsheet, for later retrieval or analysis.

Web scraping a web page involves fetching it and extracting from it. Fetching is the downloading of a page (which a browser does when a user views a page). Therefore, web crawling is a main component of web scraping, to fetch pages for later processing. Once fetched, then extraction can take place. The content of a page may be parsed, searched, reformatted, its data copied into a spreadsheet, and so on. Web scrapers typically take something out of a page, to make use of it for another purpose somewhere else. An example would be to find and copy names and phone numbers, or companies and their URLs, to a list (contact scraping).

Web scraping is used for contact scraping, and as a component of applications used for web indexing, web mining and data mining, online price change monitoring and price comparison, product review scraping (to watch the competition), gathering real estate listings, weather data monitoring, website change detection, research, tracking online presence and reputation, web mashup and, web data integration.

Web pages are built using text-based mark-up languages (HTML and XHTML), and frequently contain a wealth of useful data in text form. However, most web pages are designed for human end-users and not for ease of automated use. As a result, specialized tools and software have been developed to facilitate the scraping of web pages.

Newer forms of web scraping involve listening to data feeds from web servers. For example, JSON is commonly used as a transport storage mechanism between the client and the web server.

There are methods that some websites use to prevent web scraping, such as detecting and disallowing bots from crawling (viewing) their pages. In response, there are web scraping systems that rely on using techniques in DOM parsing, computer vision and natural language processing to simulate human browsing to enable gathering web page content for offline parsing.

[Web scraping](https://en.wikipedia.org/wiki/Web_scraping)
