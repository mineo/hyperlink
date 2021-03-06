# Hyperlink Changelog

## dev (not yet released)

* *None so far*

## 17.2.1

*(June 18, 2017)*

A small bugfix release after yesterday's big changes. This patch
version simply reverts an exception message for parameters expecting
strings on Python 3, returning to compliance with Twisted's test
suite.

## 17.2.0

*(June 17, 2017)*

Fixed a great round of issues based on the amazing community review
(@wsanchez and @jvanasco) after our first listserv announcement and
[PyConWeb talk](https://www.youtube.com/watch?v=EIkmADO-r10).

* Add checking for invalid unescaped delimiters in parameters to the
  `URL` constructor. No more slashes and question marks allowed in
  path segments themselves.
* More robust support for IDNA decoding on "narrow"/UCS-2 Python
  builds (e.g., Mac's built-in Python).
* Correctly encode colons in the first segment of relative paths for
  URLs with no scheme set.
* Make URLs with empty paths compare as equal (`http://example.com`
  vs. `http://example.com/`) per RFC 3986. If you need the stricter
  check, you can check the attributes directly or compare the strings.
* Automatically escape the arguments to `.child()` and `.sibling()`
* Fix some IPv6 and port parsing corner cases.

## 17.1.1

* Python 2.6 support
* Added LICENSE
* Automated CI and code coverage
* When a host and a query string are present, empty paths are now
  rendered as a single slash. This is slightly more in line with RFC
  3986 section 6.2.3, but might need to go further and use an empty
  slash whenever the authority is present. This also better replicates
  Twisted URL's old behavior.

## 17.1.0

* Correct encoding for username/password part of URL (userinfo)
* Dot segments are resolved on empty URL.click
* Many, many more schemes and default ports
* Faster percent-encoding with segment-specific functions
* Better detection and inference of scheme netloc usage (the presence
  of `//` in URLs)
* IPv6 support with IP literal validation
* Faster, regex-based parsing
* URLParseError type for errors while parsing URLs
* URL is now hashable, so feel free to use URLs as keys in dicts
* Improved error on invalid scheme, directing users to URL.from_text
  in the event that they used the wrong constructor
* PEP8-compatible API, with full, transparent backwards compatibility
  for Twisted APIs, guaranteed.
* Extensive docstring expansion.

## Pre-17.0.0

* Lots of good features! Used to be called twisted.python.url
