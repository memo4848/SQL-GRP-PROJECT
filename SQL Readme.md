-- Authors table
CREATE TABLE authors (
  id INT PRIMARY KEY,
  name VARCHAR(100) NOT NULL
);

-- Publishers table
CREATE TABLE publishers (
  id INT PRIMARY KEY,
  name VARCHAR(100) NOT NULL
);

-- Books table
CREATE TABLE books (
  id INT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  author_id INT NOT NULL,
  publisher_id INT NOT NULL,
  publication_date DATE,
  price DECIMAL(10, 2),
  FOREIGN KEY (author_id) REFERENCES authors(id),
  FOREIGN KEY (publisher_id) REFERENCES publishers(id)
);

-- Customers table
CREATE TABLE customers (
  id INT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(255) NOT NULL UNIQUE
);

-- Orders table
CREATE TABLE orders (
  id INT PRIMARY KEY,
  customer_id INT NOT NULL,
  order_date DATE NOT NULL,
  total DECIMAL(10, 2),
  FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- Order Items table
CREATE TABLE order_items (
  id INT PRIMARY KEY,
  order_id INT NOT NULL,
  book_id INT NOT NULL,
  quantity INT NOT NULL CHECK (quantity > 0),
  FOREIGN KEY (order_id) REFERENCES orders(id),
  FOREIGN KEY (book_id) REFERENCES books(id)
);
