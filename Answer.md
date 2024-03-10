Question 1: Explained the relationship between "Product" and "Product_Category" entities.

The relationship between "Product" and "Product_Category" entities is one-to-many. This means:

A single Product Category can have many Products associated with it (e.g., a "Clothing" category can have shirts, pants, jackets, etc.).
A single Product can only belong to one Product Category (e.g., a specific shirt cannot be in both "Clothing" and "Electronics").

Question.2 How could you ensure that each product in the "Product" table has a valid category assigned to it?

There are two main ways to ensure each product in the "Product" table has a valid category assigned:

Foreign Key Constraint: This involves creating a foreign key on the "category_id" column in the "Product" table. This foreign key would reference the primary key of the "Product_Category" table. This ensures any value entered in "category_id" must exist as a valid category ID in "Product_Category".

Not Null Constraint: This involves creating a NOT NULL constraint on the "category_id" column in the "Product" table. This simply ensures the "category_id" field cannot be left empty for any product.


Question.3 Create schema  in any Database script or any ORM (Object Relational Mapping).?
CREATE TABLE Product_Category (
  id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  description TEXT,
  created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE Product (
  id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  description TEXT,
  sku VARCHAR(255) NOT NULL,
  category_id INT FOREIGN KEY REFERENCES Product_Category(id),
  price DECIMAL(10, 2) NOT NULL,
  created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);
