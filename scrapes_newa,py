import requests
from bs4 import BeautifulSoup

def scrape_headlines(url):
    try:
        response = requests.get(url)
        response.raise_for_status()  # Check for request errors
        soup = BeautifulSoup(response.text, 'html.parser')
        
        # Adjust tag/class selector based on the news website's HTML structure
        headlines = soup.find_all('h2')
        
        with open('headlines.txt', 'w', encoding='utf-8') as file:
            for headline in headlines:
                text = headline.get_text().strip()
                if text:
                    file.write(text + '')
        print("Headlines saved successfully.")
    except requests.exceptions.RequestException as e:
        print(f"Request error: {e}")
    except Exception as e:
        print(f"An error occurred: {e}")

if __name__ == "__main__":
    news_url = "https://edition.cnn.com"  # Replace this with the actual news site URL
    scrape_headlines(news_url)
