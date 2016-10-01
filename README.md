PHP Simple HTML DOM Parser
===
A HTML DOM parser written in PHP5+ let you manipulate HTML in a very easy way!

Requirement & Features:
-----------------------
 
- A HTML DOM parser written in PHP5+ let you manipulate HTML in a very easy way!
- Require PHP 5+.
- Supports invalid HTML.
- Find tags on an HTML page with selectors just like [jQuery](http://jquery.com).
- Extract contents from HTML in a single line.

Download & Documents:
--------------------

- Download latest version form [Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=218559).
- Read [Online Document](http://simplehtmldom.sourceforge.net/manual.htm).

Quick Start:
-----------

### Get HTML elements

```php
// Create DOM from URL or file
$html = file_get_html('http://www.google.com/');

// Find all images 
foreach($html->find('img') as $element) 
       echo $element->src . '<br>';

// Find all links 
foreach($html->find('a') as $element) 
       echo $element->href . '<br>';
```

### Modify HTML elements

```php
// Create DOM from string
$html = str_get_html('<div id="hello">Hello</div><div id="world">World</div>');

$html->find('div', 1)->class = 'bar';

$html->find('div[id=hello]', 0)->innertext = 'foo';

echo $html; // Output: <div id="hello">foo</div><div id="world" class="bar">World</div>
```

### Extract contents from HTML

```php
// Dump contents (without tags) from HTML
echo file_get_html('http://www.google.com/')->plaintext; 
```

### Scraping Slashdot!

```php
// Create DOM from URL
$html = file_get_html('http://slashdot.org/');

// Find all article blocks
foreach($html->find('div.article') as $article) {
    $item['title']     = $article->find('div.title', 0)->plaintext;
    $item['intro']    = $article->find('div.intro', 0)->plaintext;
    $item['details'] = $article->find('div.details', 0)->plaintext;
    $articles[] = $item;
}

print_r($articles);
```

Feedback:
--------

- [Feature Request Tracker](http://sourceforge.net/tracker/?group_id=218559&atid=1044040).
- [Bug Tracking System](http://sourceforge.net/tracker/?group_id=218559&atid=1044037).
- [Discussion Forums](http://sourceforge.net/forum/?group_id=218559).
- [Contact Author](mailto:me578022@users.sourceforge.net).

Author:
------
Author: S.C. Chen (me578022@gmail.com)
Original idea is from Jose Solorzano's [HTML Parser for PHP 4](http://php-html.sourceforge.net/). 
Contributions by: Yousuke Kumakura (Attribute Filters)
