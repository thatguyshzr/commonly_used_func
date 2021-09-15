## Basic functions
Simple functions you don't want to bother typing.

### prime number


```python
def prime(num):
    '''
    returns True if num is prime, else return False
    -----------------------------------------------
    Parameters:
        num: [int, float] number to check for prime
    -----------------------------------------------
    Usage:
        >>> print(prime(6))
        output: False
    '''
    if isinstance(num, int):
        if num > 1:
            for j in range(2, num):
                if (num%j == 0):
                    return False
            else:
                return True
    else:
        return "Number not an integer"
```


### odd even


```python
def odd_even(num):
    '''
    returns "even" if num is even, else return "odd"
    ------------------------------------------------
    Parameters:
        num: [int, float] number to detect odd even for
    ------------------------------------------------
    Usage:
        >>> print(odd_even(4))
        output: even
    '''
    if isinstance(num, int) or isinstance(num, float):
        if num%2==0:
            return 'even'
        else:
            return 'odd'

    else:
        return "Input needs to be integer or float"

```

### sigmoid


```python
from math import exp

def sigmoid(num):
    '''
    return sigmoid of given number or array
    ---------------------------------------
    Parameters:
        num: [int, float, numpy array]
    ---------------------------------------
    Usage:
        >>> print(sigmoid(5))
        output: 0.9933071490757153
    '''
    return 1/(1 + exp(-num))
```

### function timer


```python
from time import time

def timer(func):
    '''
    returns time taken to run the function in seconds
    -------------------------------------------------
    Parameters:
        func: functions to calculate time for
    -------------------------------------------------
    Usage:
        >>> def sum(a,b):
                return a+b
        >>> print(timer(sum(1,2)))
        output: 0.0
    '''
    start= time()
    func
    return time()-start


# example
def sum(a,b):
    return a+b

print(timer(sum(1,2)))
```

### Check if image


```python
def check_img(file):
	'''
	returns:
		True: if image
		False: if not an image
	'''
	if file.endswith(tuple(['jpg', 'jpeg', 'png', 'PNG', 'JPG', 'JPEG'])):
		return True
	else:
		return False
```

----------------------------------------
## For reference

### argument parser


```python
import argparse

# Create the parser and add arguments
parser = argparse.ArgumentParser()
# Cast the input to int 
parser.add_argument('--f', '--first', type=int, help="first number",
                    required=False, default= 2)
parser.add_argument('--s', '--second', type=int, help="second number",
                    required=False, default= 3)

# Parse and print the results
args = parser.parse_args()

def sum(a, b):
    return a+b

print('Output: ',sum(args.f, args.s))

# example:
# run in command prompt
# >>> python file_name.py --f 3 --s 4
# >>> python file_name.py --first 3 --second 4
# >>> Output: 7
```

### virtual env
run in cmd


```python
# create virtual environment named "env"
py -m venv env

# activate virtual env
.\env\Scripts\activate

# deactivate virtual env
deactivate
```

### open text file


```python
with open('file.txt') as f:
    content = f.read()
```

### reverse a list


```python
x= [1,2,3,4,5]
x[::-1]

# [5,4,3,2,1]
```

### local image to colab
upload local image to google colab


```python
def upload_files()
    from google.colab import files
    uploaded = files.upload()
    for k, v in uploaded.items():
        open(k, 'wb').write(v)
    return list(uploaded.keys())

my_images= uploaded_files
```

### Create folder is it doesn't exist

```python
import os

if not os.path.exists('folder_name'):
    os.makedirs('folder_name')
```

---------------------------------------------------------------
## Library specific functions



### scrape site (BeautifulSoup)


```python
# importing the libraries
from bs4 import BeautifulSoup
import requests

def scrape_site(url, prettify= False):
    '''
    return 'bs4.BeautifulSoup' or str of url content
    ------------------------------------------------
    Parameters:
        url: url of site to be scraped
        prettify: [boolean] turns a Beautiful Soup parse tree into a nicely formatted
                  Unicode string, with a separate line for each tag and each string
                  values:
                      True: return prettified string
                      False: return 'bs4.BeautifulSoup' object of the url
    ------------------------------------------------
    Usage:
        >>> print(scrape_site(url="https://en.wikipedia.org/wiki/HTML", prettify= True))
    '''

    # Make a GET request to fetch the raw HTML content
    html_content = requests.get(url).text

    # Parse the html content
    soup = BeautifulSoup(html_content, "html.parser")
    
    if prettify:
        return soup.prettify()
    else:
        return soup

# example
print(scrap_site(url="https://en.wikipedia.org/wiki/HTML", prettify= False).title.text)
```
