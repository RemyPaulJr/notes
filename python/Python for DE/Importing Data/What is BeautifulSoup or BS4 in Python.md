
We seen that we can scrape data from the web using packages like urllib and requests, but this returns HTML that is a mix of unstructured and structured.

Structured data:
- Has pre-defined data model, or organized in a defined manner
Unstructured data: 
- Has neither of the structured data properties

If we want to turn this HTML into useful data we need to parse it and extract structured data from it.

We can do this with a python package called **BeautifulSoup**.

In web development, the term **"tag soup"** refers to structurally or syntactically incorrect HTML code written for a web page. What Beautiful Soup does best is to make tag soup beautiful again and to extract information from it with ease!

The main object created and queried when using this package is called BeautifulSoup and it has a very important associated method called **prettify**.

Example:
```python
from bs4 import BeautifulSoup
import requests

url = 'https://www.crummy.com/software/BeautifulSoup/'
r = requests.get(url)
html_doc = r.text
soup = BeautifulSoup(html_doc)
```

Then we can print soup but prettified:
```python
print(soup.prettify())
```
Output
```html
!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" "http://www.w3.org/TR/REC-html40/transitional.dtd">
<html>
	<head> 
		<meta content="text/html; charset=utf-8" http-equiv="Content-Type"/>    <title> Beautiful Soup: We called him Tortoise because he taught us. </title> <link href="mailto:leonardr@segfault.org" rev="made"/> 
		<link href="/nb/themes/Default/nb.css" rel="stylesheet" type="text/css"/> 
		<meta content="Beautiful Soup: a library designed for screen-scraping HTML and XML." name="Description"/> 
		<meta content="Markov Approximation 1.4 (module: leonardr)" name="generator"/> 
		<meta content="Leonard Richardson" name="author"/> 
		</head> 
		<body alink="red" bgcolor="white" link="blue" text="black" vlink="660066"> 
		<img align="right" src="10.1.jpg" width="250"/> 
		<br/> 
		<p>
```

If we don't need the entire HTML of a webpage, BeautifulSoup has many methods we can use to extract specific portions.

Examples:

To grab the title:
```python
print(soup.title)
```
- Output:
```html
<title>Beautiful Soup: We called him Tortoise because he taught us. </title>
```


Grab the text:
```python
print(soup.get_text)
```
- Output:
```text
Beautiful Soup: We called him Tortoise because he taught us.You didn't write that awful page. You're just trying toget some data out of it. Beautiful Soup is here to help. Since 2004, it's been saving programmers hours ordays of work on quick-turnaround screen scraping projects.
```

- find_all() - finds all elements in the document that match the specified criteria and returns them as a list
```python
for link in soup.find_all('a'):
	print(link.get('href'))
```

Output:
```text
bs4/download/
#Download
bs4/doc/
#HallOfFame
https://code.launchpad.net/beautifulsoup
https://groups.google.com/forum/?fromgroups#!forum/beautifulsoup
http://www.candlemarkandgleam.com/shop/constellation-games/
http://constellation.crummy.com/Constellation%20Games%20excerpt.html
https://groups.google.com/forum/?fromgroups#!forum/beautifulsoup
https://bugs.launchpad.net/beautifulsoup/
http://lxml.de/http://code.google.com/p/html5lib/
```

