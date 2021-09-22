---
layout: single
title: Simple Web Scrapper
excerpt: "Mi primer scrapper en Python. Queda mucho por aprender, voy estar haciendo proyectos más complejos con el tiempo."
date: 2021-05-22
classes: wide
header:
  teaser: /assets/images/scraper/scrp2.png
  teaser_home_page: true
  icon: /assets/images/python.png
categories:
  - programing
tags:  
  - python
---

Un scrapper simple hecho en python, en el que se obtiene las entradas de un blog mostrando el título, parte de su contenido y el link de la entrada.

![scrp](/assets/images/scraper/scrp2.png)



Más adelante voy estar haciendo programas mas complejos y mostrando estadísticas de los datos obtenidos.


```python

from bs4 import BeautifulSoup
import requests


html_text = requests.get(
        'https://www.cyberciti.biz/'
).text

soup = BeautifulSoup(html_text, 'lxml')

links = soup.find_all(href=True, rel=True)

print("""
Recent Entries:
""")

for link in links:
  if soup.find(rel=True) and bool(link.text):
    title = link.text
    extra = soup.find('div', class_ = "post_content").text
    post_link = link['href']
    
    print(f'\nTitle: {title}\n {extra}\nLink: {post_link}\n')

```
