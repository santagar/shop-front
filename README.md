# shop-front

It's just a shopping cart experiment using Vue.js.

- [See it live!](http://shop.santagar.com)

This project is built with [vue-cli](https://github.com/vuejs/vue-cli) and [vuex](https://github.com/vuejs/vuex).

Also, I suggest you to use [vue-devtools](https://github.com/vuejs/vue-devtools) if you want a see how everything happens.

### How cart works

- Products can be added to the cart if they have an item available on stock.
- Products added to the cart must be removable.
- Checkout must be disabled if cart **total** is over user **limit**.
- If a product already exists on the cart, its counter should be updated.
- All products have a shipping price. **shipping** is defined by the highest shipping price of products added to cart.

### How promotions work

- 30% OFF should reduce 30% of the costs on **subtotal**.
- $100.00 Discount should reduce $100.00 of **total**.
- Free Shipping should set **shipping** to zero.
- +$100.00 on limit should increase user **limit** by $100.00.

## Project setup
```
yarn install
```

### Serve with hot reload
```
yarn run serve
```

### Build for production with minification
```
yarn run build
```

### Deploy static on AWS

More info. Deploy Setup
```
yarn run deploy
```

### Run your tests
```
yarn run test
```

### Lints and fixes files
```
yarn run lint
```

### Run your end-to-end tests
```
yarn run test:e2e
```

### Run your unit tests
```
yarn run test:unit
```

## Deploy Setup

AWS cli is required.

* Create **Amazon S3 Bucket** with name using domain (i.e: *shop.santagar.com*) in order to allow direct association from **Route53** and apply following **Bucket Policy**:

``` bash
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "PublicReadAccess",
			"Effect": "Allow",
			"Principal": "*",
			"Action": "s3:GetObject",
			"Resource": "arn:aws:s3:::shop.santagar.com/*"
		}
	]
}

```

* Configure to use like website in **Static website hosting**

* Create a **Record Set** type A with alias associated to **S3 website endpoint** (i.e: *shop.santagar.com*)

* Upload `/dist` folder to S3 Bucket indicated on deploy script in `package.json`

``` bash
yarn run deploy
```
