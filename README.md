
## Getting Started

chromedriver.exe does *not* come w/ Selenium; easy to just google and download


```python
from selenium import webdriver

path_to_chromedriver = '../src/chromedriver.exe'
browser = webdriver.Chrome(path_to_chromedriver)
url_requires_http = 'https://www.google.com'
browser.get(url_requires_http)
```

![css selector in Chrome developer tool](src/inspect_element_css_selector.png)

``` css selector = tag#id.class[attribute=value] ```


```python
search_bar = browser.find_element_by_css_selector("input#lst-ib.gsfi[title = 'Search']")
search_bar.send_keys('text')
search_bar.submit() 
# or browser.find_element_by_css_selector("input[value='Google Search']").click()
```


```python
## /: selects fr the root node ;'/head' does NOT work, '/html/head' works
## .//: select fr current node
abs_path = 'html/head'
relative_path = './/head'
list_of_elems_in_node = browser.find_elements_by_xpath(relative_path)
```

#### find_element vs find_elementS


```python
first_elem = browser.find_element_by_xpath(relative_path)
```


```python
divs_elems_in_first_elem = first_elem.find_elements_by_xpath('.//div')
```


```python
from selenium.webdriver.common.keys import Keys
def open_new_tab(anchor_elem):
    anchor_elem.send_keys(Keys.CONTROL + Keys.RETURN)
open_windows_tabs = browser.window_handles    
newest_window_tab = open_windows_tabs[-1]
browser.switch_to_window(newest_window_tab)
```


```python
browser.current_url; browser.page_source; browser.window_handles;
```


```python
def show_attr(elements):
    for e in elements:
        attr = ['class', 'name', 'id', 'title']
        for i, attr in enumerate(attr):
            print(i)
            print(attr, '=', e.get_attribute(attr))
    text_btwn_tags = e.text; print(text_btwn_tags)
```
