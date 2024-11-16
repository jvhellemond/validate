# Validate

Validation middleware for use with the Hono framework.


## Usage

```js
import {Hono} from "@hono/hono";
import validate, {Schema as µ} from "@jvhellemond/validate";

app.get(
	"/",
	validate("query", {
		offset:   µ.isOptional.coerce(Number).isInteger.isBetween(0, 99_999),
		limit:    µ.isOptional.coerce(Number).isInteger.isBetween(10, 500),
		sortDesc: µ.isOptional.coerce([Number, Boolean]).isBoolean,
		sortBy:   µ.isOptional.lengthIsBetween(1, 50)
	}),
	ctx => {
		// ...
	}
);
```
