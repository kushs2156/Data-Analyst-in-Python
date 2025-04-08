- A `customer` table with information about each customer
- A `cust_tax_info` table with customers unique tax IDs
- An `orders` table with information about each order
- A `products` table with details about each unique product sold
- An `inventory` table with information on how much total inventory is available to sell for each product

| Relationship | Example                                                  |
| ------------ | -------------------------------------------------------- |
| One-to-many  | The relationship between the `customers` and `orders`.   |
| One-to-one   | The relationship between `customer` and `cust_tax_info`. |
| One-to-one   | The relationship between `products` and `inventory`.     |
| One-to-many  | The relationship between the `products` and `orders`.    |


