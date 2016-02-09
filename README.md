# handy-regex-patterns

A few handy RegEx patterns, mostly for use on the web.  

- Use with [flags](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) as needed. 
- Use one of the JavaScript methods below to test with these patterns.
   - [`RegExp.prototype.test(str)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test)
   - [`String.prototype.match(regexp)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match)
   - [`String.prototype.search(regexp)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/search)
   - [`String.prototype.replace(regexp)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

### Web

- Match a URL:  
  ```javascript
  /^(?:https?:\/\/)?(?:[\w]+\.)([a-zA-Z\.]{2,6})([\/\w\.-]*)*\/?/
  ```
  - The use of [non-capturing groups](http://www.regular-expressions.info/brackets.html) causes the first returned group to be the domain, not the protocol or subdomain.

- Match an IP address:  
  ```javascript
  /^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/
  ```

- Match a Hex Value:  
  ```javascript
  /^#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3})$/
  ```
  - Matches any valid 3- or 6-character hex sequence. `#` symbol is optional.
    - e.g. #fff, #6a6a6a, 000, c7e

### Web Forms

- Validate Username: 
  ```javascript
  /^[a-z0-9_-]{3,16}$/i
  ```
  - Username must contain between 3 and 16 characters. Characters are limited to number, letters, the hyphen (-), and the underscore (_). The `i` flag allows for capital as well as lowercase letters.

- Validate Password: 
  ```javascript
  /^(?=.*[A-Z])(?=.*[a-z])(?=.*[0-9])(.{6,})$/
  ```
  - Password must contain at least 6 characters. The password must contain at least one capital letter, one lowercase letter, and one number.

- Match an email address:  
  ```javascript
  /^[_A-Za-z0-9-]+(\.[_A-Za-z0-9-]+)*@[A-Za-z0-9]+(\.[A-Za-z0-9]+)*(\.[A-Za-z]{2,})$/
  ```
- Match a phone number:  
  ```javascript
  /^(([0-9]{1})*[- .(]*([0-9]{3})[- .)]*[0-9]{3}[- .]*[0-9]{4})+$/
  ```

- Validate Date (MM/DD/YYYY):  
  ```javascript
  /^(0?[1-9]|1[012])[- /.](0?[1-9]|[12][0-9]|3[01])[- /.](19|20)?[0-9]{2}$/
  ```

- Validate all major Credit Cards (Visa, Amex, Discover, Mastercard):  
  ```javascript
  /^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14}|6011[0-9]{12}|3(?:0[0-5]|[68][0-9])[0-9]{11}|3[47][0-9]{13})$/
  ```

### File Manipulation

- Trim whitespace (replace with nothing):  
  ```javascript
  /^[ \t]+|[ \t]+$/  Finds leading and trailing spaces and tabs

  /^[\s]+|[\s]+$/    Finds leading and trailing spaces, tabs, and return/new line characters 
  ```
