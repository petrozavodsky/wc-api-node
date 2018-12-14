# WooCommerce API - Node.js Client

A Node.js wrapper for the WooCommerce REST API. Easily interact with the WooCommerce REST API using this library.

[![build status](https://secure.travis-ci.org/woocommerce/wc-api-node.svg)](http://travis-ci.org/woocommerce/wc-api-node)
[![dependency status](https://david-dm.org/woocommerce/wc-api-node.svg)](https://david-dm.org/woocommerce/wc-api-node)
[![npm version](https://img.shields.io/npm/v/woocommerce-api.svg)](https://www.npmjs.com/package/woocommerce-api)

## Installation

```
npm install --save woocommerce-api-heades-suport
```

## Getting started

Use jwt tikens
.

Check out the WooCommerce API endpoints and data that can be manipulated in <http://woocommerce.github.io/woocommerce-rest-api-docs/>.

## Setup

Setup for the new WP REST API integration (WooCommerce 2.6 or later):

```js
var WooCommerceAPI = require('woocommerce-api');

var WooCommerce = new WooCommerceAPI({
  url: 'http://example.com',
  tokenJwt: 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX',
  wpAPI: true,
  version: 'wc/v1'
});
```

Setup for the old WooCommerce legacy API:

```js
var WooCommerceAPI = require('woocommerce-api');

var WooCommerce = new WooCommerceAPI({
  url: 'http://example.com',
  tokenJwt: 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX',
  version: 'v3'
});
```

### Options

|       Option      |    Type   | Required |                                               Description                                                |
|-------------------|-----------|----------|----------------------------------------------------------------------------------------------------------|
| `url`             | `String`  | yes      | Your Store URL, example: http://woo.dev/                                                                 |
| `tokenJwt`        | `String`  | yes      | JWT token                                                                                    |
| `wpAPI`           | `Bool`    | no       | Allow requests to the WP REST API (WooCommerce 2.6 or later)                                             |
| `wpAPIPrefix`     | `String`  | no       | Custom WP REST API URL prefix, used to support custom prefixes created with the `rest_url_prefix` filter |
| `version`         | `String`  | no       | API version, default is `v3`                                                                             |
| `verifySsl`       | `Bool`    | no       | Verify SSL when connect, use this option as `false` when need to test with self-signed certificates      |
| `encoding`        | `String`  | no       | Encoding, default is 'utf-8'                                                                             |
| `queryStringAuth` | `Bool`    | no       | When `true` and using under HTTPS force Basic Authentication as query string, default is `false`         |
| `port`            | `string`  | no       | Provide support for URLs with ports, eg: `8080`                                                          |
| `timeout`         | `Integer` | no       | Define the request timeout                                                                               |

## Methods

|   Params   |    Type    |                         Description                          |
|------------|------------|--------------------------------------------------------------|
| `endpoint` | `String`   | WooCommerce API endpoint, example: `customers` or `order/12` |
| `data`     | `Object`   | JS object, will be converted to JSON                         |
| `callback` | `Function` | Callback function. Returns `err`, `data` and `res`           |

### GET

- `.get(endpoint)`
- `.get(endpoint, callback)`

### POST

- `.post(endpoint, data)`
- `.post(endpoint, data, callback)`

### PUT

- `.put(endpoint, data)`
- `.put(endpoint, data, callback)`

### DELETE

- `.delete(endpoint)`
- `.delete(endpoint, callback)`

### OPTIONS

- `.options(endpoint)`
- `.options(endpoint, callback)`

## Promified Methods

Every method can be used in a promified way just adding `Async` to the method name. Like in:

```js
WooCommerce.getAsync('products').then(function(result) {
  return JSON.parse(result.toJSON().body);
});
```

## Release History

- 2018-12-14 - v1.1.0 - Remove secret key
