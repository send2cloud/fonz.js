fonz.js
=========

[![Build Status](https://travis-ci.org/dvx/fonz.js.svg?branch=master)](https://travis-ci.org/dvx/fonz.js)

A node library that accurately validates phone numbers. It tries its best to abide by NANPA standards, but international numbers are not yet supported.

### Why fonz.js?
Fonz.js validates whether or not an input is a valid North American phone number according to the [North American Numbering Plan Administration](https://www.nationalnanpa.com/index.html). It verifies area codes, exchange codes, and station codes. To do this verification, all non-numeric characters are stripped. In some cases, results are better than Google's libphonenumber. For example, the following (correctly) do not pass validation using fonz.js:

- 310-911-1234
- 770-555-0150
- 949-411-0110
- 770-555-1212

Other validators incorrectly mark them as valid. To read more about how and why fonz.js was written, check out the blog post [here](https://dvt.name/2017/04/25/fonz-js-a-better-phone-verification-library/).

## Installation

  `npm install fonz.js`

## Usage

    var fonz = require('fonz.js');

    if (fonz.validate('123-456-7890')) {
      // this will fail validation as 123 is an invalid area code
    }
    
    
  Non-numeric characters are stripped:
  
    // this is fine!
    if (fonz.validate('xyz-4-0-4-|-4-5-6-!-7-8-9-0-abc-')) { 
      // this is a valid number!
    }
    
  Leading with a the valid country code of `1` is perfectly acceptable:
  
    if (fonz.validate(13104439021)) { 
      // this is a valid number!
    }
  
  The `validate()` function will always return `true` or `false`.


## Tests

  `npm test`


## Contributing

Feel free to contribute! Bug fixes or new features are always welcome.
