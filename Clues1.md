
# Full Stack Data Visualization Project Setup

## Backend Setup (Spring Boot with H2 Database)

1. Create a new Spring Boot project using Spring Initializr (https://start.spring.io/)
   - Choose Maven as the build tool
   - Select Java as the language
   - Choose the latest stable Spring Boot version
   - Add dependencies: Spring Web, Spring Data JPA, H2 Database

2. Open the project in your preferred IDE

3. Configure H2 Database in `application.properties`:
   ```
   spring.datasource.url=jdbc:h2:mem:testdb
   spring.datasource.driverClassName=org.h2.Driver
   spring.datasource.username=sa
   spring.datasource.password=password
   spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
   spring.h2.console.enabled=true
   ```

4. Create entity classes for Customers, Products, and Orders

5. Create repository interfaces for each entity

6. Implement service classes for business logic

7. Create REST controllers to expose API endpoints

## Frontend Setup (React)

1. Create a new React project:
   ```
   npx create-react-app frontend
   cd frontend
   ```

2. Install necessary dependencies:
   ```
   npm install axios chart.js react-chartjs-2
   ```

3. Create components for each chart type

4. Implement API calls to fetch data from the backend

5. Use react-chartjs-2 to create visualizations

## Integration and Development

1. Implement CORS configuration in the Spring Boot backend

2. Test API endpoints using tools like Postman

3. Connect React components to the backend API

4. Style your application and add any additional features

## Deployment

1. Build the React frontend:
   ```
   npm run build
   ```

2. Copy the build files to the `src/main/resources/static` folder of your Spring Boot project

3. Build the Spring Boot application:
   ```
   mvn clean package
   ```

4. Deploy the resulting JAR file to your chosen hosting service


Now, let's create some sample data to be added to the H2 database using SQL. I'll provide SQL statements for creating tables and inserting some initial data.



```sql
-- Create Customers table
CREATE TABLE customers (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(255),
    last_name VARCHAR(255),
    email VARCHAR(255),
    created_at TIMESTAMP,
    city VARCHAR(255)
);

-- Create Products table
CREATE TABLE products (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255),
    price DECIMAL(10, 2)
);

-- Create Orders table
CREATE TABLE orders (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    customer_id BIGINT,
    total_price DECIMAL(10, 2),
    created_at TIMESTAMP,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- Insert sample data into Customers table
INSERT INTO customers (first_name, last_name, email, created_at, city) VALUES
('John', 'Doe', 'john.doe@example.com', '2023-01-01 10:00:00', 'New York'),
('Jane', 'Smith', 'jane.smith@example.com', '2023-01-15 11:30:00', 'Los Angeles'),
('Bob', 'Johnson', 'bob.johnson@example.com', '2023-02-01 09:15:00', 'Chicago'),
('Alice', 'Brown', 'alice.brown@example.com', '2023-02-15 14:45:00', 'Houston'),
('Charlie', 'Davis', 'charlie.davis@example.com', '2023-03-01 16:20:00', 'Phoenix');

-- Insert sample data into Products table
INSERT INTO products (title, price) VALUES
('T-shirt', 19.99),
('Jeans', 49.99),
('Sneakers', 79.99),
('Backpack', 39.99),
('Watch', 99.99);

-- Insert sample data into Orders table
INSERT INTO orders (customer_id, total_price, created_at) VALUES
(1, 69.98, '2023-01-10 13:30:00'),
(2, 119.98, '2023-01-20 15:45:00'),
(3, 159.97, '2023-02-05 11:00:00'),
(4, 89.98, '2023-02-20 10:15:00'),
(5, 199.98, '2023-03-05 14:30:00'),
(1, 139.97, '2023-03-15 16:00:00'),
(2, 179.98, '2023-04-01 09:45:00'),
(3, 99.99, '2023-04-10 12:30:00'),
(4, 129.98, '2023-04-20 11:15:00'),
(5, 229.97, '2023-05-01 15:00:00');

```

To implement this project, follow these additional steps:

1. Create the necessary Java classes (entities, repositories, services, and controllers) in your Spring Boot project.

2. Implement the required API endpoints in your controllers to fetch the data for each chart type.

3. In your React frontend, create components for each chart type and use axios to fetch data from your API endpoints.

4. Use react-chartjs-2 to create the visualizations based on the fetched data.

5. Style your application and add any additional features or interactivity as needed.

6. Test your application thoroughly, ensuring that all charts are displaying correctly and updating with real-time data.

7. Once everything is working as expected, follow the deployment steps outlined in the project setup instructions to host your application.

Remember to adapt the sample data and chart implementations to match the specific requirements of the evaluation task. The provided SQL data is a simplified version to get you started, but you may need to expand it to fully meet the task requirements.

