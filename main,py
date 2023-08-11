import requests
import xml.etree.ElementTree as ET

print("Input your Steam API key.")
print("Note: You can register your Steam API key by following the link 'https://steamcommunity.com/dev/apikey'.")
print("Steam API key:")
api_key = input()
url = "https://api.steampowered.com/IPlayerService/GetOwnedGames/v0001/?key={}&steamid=76561198104140983&format=xml&include_appinfo=1&include_played_free_games=1".format(api_key)

try:
    response = requests.get(url)
    response.raise_for_status() 
    content = response.content
    content = content.decode("utf-8")
except requests.exceptions.RequestException as e:
    print("An error occurred while executing the request:", e)

root = ET.fromstring(content)
name_element = root.find("./games/messages/name")
names = []
for message_element in root.findall(".//name"):
    name = message_element.text
    names.append(name)

names.sort()
n = 1
for name in names:
    print(n, name)    
    n = n + 1
