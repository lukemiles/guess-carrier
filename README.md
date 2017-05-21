## What is this?
This is a fork of [sailrish's](https://github.com/sailrish) [shipit](https://github.com/sailrish/shipit) to only include the carrier-guesser bits.

### Using the Carrier Guesser
There's usually only one carrier that matches a tracking number (UPS is the only carrier that uses '1Z' prefix for its tracking numbers), but there are several cases, where there are multiple matches.  For example, FedEx uses a service called SmartPost, where it relies on USPS to deliver the package at the last mile.  In such cases, FedEx provides tracking through most of the package's journey, and then USPS either takes over, or provides duplicate tracking in the last leg.  The tracking number used is the same between the two carriers.  Similar situation with UPS Mail Innovations as well.  Therefore, the `guessCarrier()` function returns an array, and we leave it up to the user to decide manually or through other automated means which carrier is the real one or provides more accurate tracking.
```coffeescript
guessCarrier = require 'guess-carrier'
possibleCarriers = guessCarrier '1Z6V86420323794365'
[ 'ups' ]
possibleCarriers = guessCarrier '9274899992136003821767'
[ 'fedex', 'usps' ]
possibleCarriers = guessCarrier 'EC207920162US'
[ 'usps' ]
```

## Building
Clone this repo (or first fork it)
```
git clone git@github.com:lukemiles/guess-carrier.git
```
Install dependencies
```
npm install
```
Just use grunt.
```
$ grunt

. . .
. . .

  182 passing (347ms)


Done, without errors.
```

## License
Copyright &#169; 2016 Rishi Arora

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files, but excluding the `shipit-api` Heroku app mentioned above (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
