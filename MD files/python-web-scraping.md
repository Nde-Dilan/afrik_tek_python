# 🕸️ Web Scraping with Python: Mining the Internet

## Welcome to Web Scraping! 
Learn how to extract and analyze data from websites automatically - like a data ninja! 

### What We'll Learn 🎯
- What is web scraping and why it's awesome
- Key libraries (Requests, BeautifulSoup)
- Scraping techniques and best practices
- Real-world scraping projects

---

## 1. Web Scraping Basics: Your Digital Mining Tools ⛏️

### What is Web Scraping? 🤔
Web scraping is like having a super-fast assistant who can read websites and collect information for you automatically!

```python
# First, let's import our key libraries
import requests
from bs4 import BeautifulSoup
import pandas as pd
import time

# Simple example: Getting a webpage
def fetch_webpage(url):
    """Fetch a webpage and return its content"""
    try:
        response = requests.get(url)
        response.raise_for_status()  # Check for errors
        return response.text
    except requests.RequestException as e:
        return f"An error occurred: {e}"

# Test with a simple webpage
url = "http://quotes.toscrape.com"
content = fetch_webpage(url)
print("Successfully fetched the webpage!" if content else "Failed to fetch webpage")
```

### Why Web Scraping is Awesome! 🌟
```python
"""
Benefits of Web Scraping:
1. Automate data collection
2. Save hours of manual work
3. Get real-time data
4. Build powerful datasets
5. Monitor prices and changes
"""

# Example: Scraping quotes
def scrape_quotes(url):
    """Scrape quotes from quotes.toscrape.com"""
    content = fetch_webpage(url)
    soup = BeautifulSoup(content, 'html.parser')
    
    quotes = []
    for quote in soup.find_all('div', class_='quote'):
        text = quote.find('span', class_='text').text
        author = quote.find('small', class_='author').text
        quotes.append({'quote': text, 'author': author})
    
    return quotes

# Let's get some quotes!
quotes = scrape_quotes(url)
for i, quote in enumerate(quotes[:3], 1):
    print(f"\nQuote {i}:")
    print(f"📝 {quote['quote']}")
    print(f"✍️ - {quote['author']}")
```

---

## 2. Essential Tools: Your Scraping Toolkit 🧰

```python
# BeautifulSoup Basics
def soup_tutorial():
    html_example = """
    <html>
        <body>
            <h1>Welcome to Scraping</h1>
            <div class="content">
                <p class="important">This is important text</p>
                <p>This is normal text</p>
                <a href="https://example.com">Click here</a>
            </div>
        </body>
    </html>
    """
    
    soup = BeautifulSoup(html_example, 'html.parser')
    
    print("🔍 Finding Elements:")
    print(f"Title: {soup.h1.text}")
    print(f"Important text: {soup.find('p', class_='important').text}")
    print(f"Link href: {soup.a['href']}")

# Run the tutorial
soup_tutorial()
```

### 🎯 Practice: Build a Simple Scraper
```python
def scrape_weather(city):
    """Simulate weather scraping (for educational purposes)"""
    weather_data = {
        'New York': {'temp': '72°F', 'condition': 'Sunny'},
        'London': {'temp': '18°C', 'condition': 'Rainy'},
        'Tokyo': {'temp': '25°C', 'condition': 'Cloudy'}
    }
    
    return weather_data.get(city, {'temp': 'N/A', 'condition': 'City not found'})

# Test the weather scraper
cities = ['New York', 'London', 'Tokyo']
for city in cities:
    weather = scrape_weather(city)
    print(f"\n🌍 Weather in {city}:")
    print(f"🌡️ Temperature: {weather['temp']}")
    print(f"☁️ Condition: {weather['condition']}")
```

---

## 3. Best Practices: Being a Good Scraping Citizen 🤝

```python
class WebScraper:
    def __init__(self):
        self.session = requests.Session()
        self.session.headers = {
            'User-Agent': 'Mozilla/5.0 (Educational Purpose Only)'
        }
    
    def scrape_with_delay(self, urls, delay=2):
        """Scrape multiple URLs with a polite delay"""
        results = []
        
        for url in urls:
            # Be polite, wait between requests
            time.sleep(delay)
            
            try:
                response = self.session.get(url)
                results.append(response.text)
                print(f"✅ Successfully scraped: {url}")
            except Exception as e:
                print(f"❌ Failed to scrape {url}: {e}")
        
        return results

# Example usage
scraper = WebScraper()
test_urls = [
    "http://quotes.toscrape.com/page/1",
    "http://quotes.toscrape.com/page/2"
]
```

---

## 4. Real-World Project: Building a Book Scraper 📚

```python
class BookScraper:
    def __init__(self):
        self.base_url = "http://books.toscrape.com"
        self.scraper = WebScraper()
    
    def scrape_book_details(self, book_url):
        """Scrape details of a single book"""
        content = self.scraper.session.get(book_url).text
        soup = BeautifulSoup(content, 'html.parser')
        
        title = soup.find('h1').text
        price = soup.find('p', class_='price_color').text
        availability = soup.find('p', class_='availability').text.strip()
        
        return {
            'title': title,
            'price': price,
            'availability': availability
        }
    
    def scrape_category(self, category_url, limit=5):
        """Scrape books from a category"""
        books = []
        content = self.scraper.session.get(category_url).text
        soup = BeautifulSoup(content, 'html.parser')
        
        for book in soup.find_all('article', class_='product_pod')[:limit]:
            title = book.h3.a['title']
            price = book.find('p', class_='price_color').text
            books.append({'title': title, 'price': price})
        
        return books

# Test the book scraper
book_scraper = BookScraper()
science_books = book_scraper.scrape_category(
    "http://books.toscrape.com/catalogue/category/books/science_22/index.html"
)

print("\n📚 Science Books Available:")
for book in science_books:
    print(f"\n📖 {book['title']}")
    print(f"💰 {book['price']}")
```

---

## 5. Fun Project: Building a News Headline Aggregator 📰

```python
class HeadlineAggregator:
    def __init__(self):
        self.sources = {
            'Tech': 'http://example.com/tech',  # Replace with real URLs
            'Science': 'http://example.com/science',
            'Sports': 'http://example.com/sports'
        }
    
    def get_headlines(self, category):
        """Simulate getting headlines (for educational purposes)"""
        sample_headlines = {
            'Tech': [
                "New AI Breakthrough Announced",
                "Latest Smartphone Released",
                "Quantum Computing Milestone Reached"
            ],
            'Science': [
                "Mars Mission Update",
                "New Species Discovered",
                "Climate Study Released"
            ],
            'Sports': [
                "Championship Finals Today",
                "New World Record Set",
                "Star Player Signs Deal"
            ]
        }
        
        return sample_headlines.get(category, ["Category not found"])

# Test the headline aggregator
aggregator = HeadlineAggregator()
categories = ['Tech', 'Science', 'Sports']

for category in categories:
    print(f"\n📰 {category} Headlines:")
    for headline in aggregator.get_headlines(category):
        print(f"➤ {headline}")
```

---

## 🎉 Congratulations!

You've learned:
- Web scraping basics
- Using BeautifulSoup and Requests
- Best practices and ethics
- Real-world applications

### 📚 Practice Ideas
1. Build a price comparison tool
2. Create a news aggregator
3. Track product prices
4. Build a job listing scraper

### 🎯 Challenge Project: Multi-Site Data Aggregator
Create a system that:
- Scrapes data from multiple sources
- Compares prices across websites
- Tracks changes over time
- Exports data to CSV/Excel

Remember: Always check a website's robots.txt and terms of service before scraping! 🚀
