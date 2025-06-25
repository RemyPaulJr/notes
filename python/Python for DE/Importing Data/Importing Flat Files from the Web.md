
# Why important files from the web when you can download and access files locally?

The problems that can occur with this is that it's hard to reproduce code, and it's not scalable.

If you can to share your code with other Developers and Engineers then they have to download the files themselves and match the directory location in your code. This can lead to errors like downloading an older version of the file, downloading the wrong file, etc.

Or if you want to download 100 or 1000 files, this will 100x or 1000x your workflow.

## Urllib Package

This package provides the interface for fetching data across the web.

It does so with the urlopen() function.
```python
urlopen()
```
- accepts URLs instead of file names

Example:
```python
from urllib.request import urlretrieveurl

url = 'http://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-white.csv'
urlretrieve(url, 'winequality-white.csv')
```

Desired output:
```text
('winequality-white.csv', <http.client.HTTPMessage at 0x103cf1128>)
```

## HTTP requests to import files from the web

Another method we can use is an http request.

We used the urlretrieve function from urllib dot requests. Lets now unpack this a bit and, in the process, understand a few things about how the internet works. 

URL stands for Uniform or Universal Resource Locator and all they really are are references to web resources. 

The vast majority of URLs are web addresses, but they can refer to a few other things, such as file transfer protocols (FTP) and database access. We'll currently focus on those URLs that are web addresses OR the locations of websites.

Each time you go to a website, you are actually sending an HTTP request to a server. This request is known as a GET request, by far the most common type of HTTP request. 

- We are actually performing a GET request when using the function urlretrieve. 
- The ingenuity of urlretrieve also lies in fact that it not only makes a GET request but also saves the relevant data locally.

For example, to extract the html from the wikipedia home page, you import the necessary functions, specify the URL, package the GET request using the function Request, send the request and catch the response using the function urlopen.

```python
from urllib.request import urlopen, Request 

url = "https://www.wikipedia.org/"
request = Request(url)
response = urlopen(request)
html = response.read()
response.close()
```

### Using request package

Requests is one of the most downloaded Python packages of all time. And for good reason.

We can achieve the same result as the code above in only 3 lines:

```python
import requests

url = "https://www.wikipedia.org/"
r = requests.get(url)
text = r.text
```