---
title: "2019 08 17 Generating Consistent Faker Values for Testing"
date: 2020-01-11T09:28:02-06:00
draft: true
---

# Generating consistent faker values for testing

Post date: 2018-08-17

So this is good to know. I hadn't seen this before.

When using [faker.js](https://github.com/Marak/Faker.js), you can generate the exact same data each time by setting the **seed**:

```javascript
import faker from "faker"

faker.seed(123);

export const testData = {
  id: faker.number.uuid(),
  name: `${faker.name.firstName()} ${faker.name.lastName()}`,
  email: fakcer.internat.email()
}
```

Which would give the same data each time.

Keywords: JavaScript, faker, test data, testing

