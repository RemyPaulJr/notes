## Via API

What is an **API**?
An API is a set of protocols and routines for building and interacting with software, enabling you to pull data from the web.

What is **JSON**?

JSON (Javascript Object Notation) - Standard file format for transferring data through APIs.

- Key thing here is JSON files are **human-readable**! 
- They consist of name-value pairs similar to key-value pairs in Python Dictionaries.
- This format is particularly useful for server-to-browser communication without relying on Flash or Java.

#### Loading JSONs in Python

We can use the json.load() function to load a JSON file in Python.
Example:

```python
import json # import package json
with open('snakes.json', 'r') as json_file: # open connection to file
	json_data = json.load(json_file) # use json.load() function to load json file
```

The type of json_data will be a dictionary.

Since it's stored as a dictionary we can use a for loop to print the key value pairs of the json file.
Example:

```python
for key, value in json_data.items():
	print(key + ':', value)
```

output will look something like:

```python
Title: Snakes on a Plane
Country: Germany, USA, Canada
```

## Connecting to an API in Python

```python
import requests 

url = 'http://www.omdbapi.com/?apikey=72bc447a&t=hackers' # Assign URL
r = requests.get(url) # Package and send request to the URL, and catch the   response in one line of code thanks to requests
json_data = r.json() # Built in json decoder that will return a dictionary

for key, value in json_data.items():
	print(key + ':', value)
```

### Breaking down the URL

- http - making an HTTP request
- www.omdbapi.com - querying the OMDB API
- ?apikey=(apikey)
	- we need to provide an api key.
- &t=hackers
	- Query string- Query Strings are parts of URLs that do not necessarily fit into conventional a hierarchical path structure
	- t=hackers in the query string is the query we are making to the OMDB API.
		- Return data for a movie with the title(t) 'Hackers'

We knew that this was how to perform such a query from the documentation on the OMDB API's homepage. Under "Usage" here, they state explicitly that 'Send all data requests to: http:// www dot omdbapi dot com /?'

They also have a query string parameters table that shows how to query a particular title or a particular movie ID.

> [!NOTE]
> It's a regular URL! We can access this in our browser.
> More info on how to call this API can be found at https://www.omdbapi.com/

