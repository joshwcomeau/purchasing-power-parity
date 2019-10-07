# Purchasing Power Parity

[![Build Status](https://travis-ci.org/rwieruch/purchasing-power-parity.svg?branch=master)](https://travis-ci.org/rwieruch/purchasing-power-parity)

Not everyone is able to pay for the default pricings of the western world. Online products should be made affordable for everyone around the world. This package is a simple way to make [Purchasing Power Parity](https://en.wikipedia.org/wiki/Purchasing_power_parity) available in your browser. See how it could look like in your application for someone buying your product from another country:

<img width="1276" alt="screen shot 2017-11-02 at 08 40 54" src="https://user-images.githubusercontent.com/2479967/32305725-a8186744-bfa9-11e7-9d58-a074c5b34982.png">

## How to use it?

**Install:**

`npm install purchasing-power-parity`

**Use:**

```js
import fetchPPP from 'purchasing-power-parity';

let originalPrice = 99.99;
let discountPrice;

fetchPPP(OPEN_EXCHANGE_RATES_API_KEY, QUANDL_API_KEY).then((response) => {
  discountPrice = response.ppp.pppConversionFactor * originalPrice;
});
```

So you can adjust your prices when the `pppConversionFactor` goes below 1 and add an optional banner for your customers to make them aware of it. What other information is in the returned PPP object?

**ppp-object:**

```js
{
  countryCodeIsoAlpha2: "IN",
  countryCodeIsoAlpha3: "IND",
  countryName: "India",
  currenciesCountry: [{
    code: "INR",
    name: "Indian rupee",
    symbol: "₹"
  }],
  currencyMain: {
    exchangeRate: 65.06,
    code: "INR",
    name: "Indian rupee",
    symbol: "₹"
  },
  ppp: 17.536,
  pppConversionFactor: 0.2695358130956041,
}
```

The `currencyMain.exchangeRate` property is used to compute the `pppConversionFactor` by using the `ppp` property.

## Limitations

* runs only in the browser
* takes only USD as baseline

## Who uses PPP?

This node package was inspired by [Wes Bos](https://twitter.com/wesbos) who sells his courses with PPP. There are other people which make their products affordable to everyone around the world by using PPP. You can add your project/company/product/service/... to the list when you are using this package:

* [Road to React](https://roadtoreact.com/)
* ...

## Contribution

The project is in an early stage, so please feel free to contribute to it. It works, but it could be more robust and improved. If you want to know how PPP works, you can read up this [short article](https://www.sapling.com/6218206/calculate-purchasing-power-parity). I would love to see you contributing to it:

* create an Issue
* discuss with maintainers and contributors about the issue
* create a Pull Request if the issue should be solved
