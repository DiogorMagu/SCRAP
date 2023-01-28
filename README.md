import requests
from bs4 import BeautifulSoup

def get_prices(URL):
    page = requests.get(URL)
    soup = BeautifulSoup(page.content, "html.parser")
    prices = soup.find_all(class_="a-price")
    return [price.get_text() for price in prices]

URL = "https://www.amazon.com/s?k=computer+parts"
prices = get_prices(URL)
print(prices)
