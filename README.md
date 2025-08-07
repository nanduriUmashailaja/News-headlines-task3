# News-headlines-task3
Scrape top headlines from a news website.
import requests
from bs4 import BeautifulSoup

# URL of the news website (BBC News in this case)
url = "https://www.bbc.com/news"

# Send an HTTP GET request
response = requests.get(url)

# Parse the HTML content using BeautifulSoup
soup = BeautifulSoup(response.content, "html.parser")

# Find headline tags (BBC often uses <h3> with specific classes)
headlines = soup.find_all('h3')

print("Top Headlines:\n")
for i, headline in enumerate(headlines[:10], start=1):  # Get top 10
    text = headline.get_text(strip=True)
    if text:
        print(f"{i}. {text}")
