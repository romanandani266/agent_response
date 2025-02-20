# Project Requirements

# Business Requirements Document (BRD)

## Project Name: Retail Inventory Management System

### 1. Introduction
The Retail Inventory Management System project aims to develop a simple and efficient system for tracking product stock levels, predicting restocking needs, and minimizing waste. This system is designed to enhance the inventory management processes for retail partners, the PepsiCo supply chain team, and warehouse managers.

### 2. Business Objectives
- Develop a user-friendly inventory management system that provides real-time tracking of product stock levels.
- Implement automated restocking alerts to ensure optimal stock levels.
- Analyze sales trends to improve sales forecasting and minimize waste.

### 3. Scope
#### In Scope:
- Development of a web-based inventory tracking system.
- Implementation of automated stock alert notifications.
- Integration of sales trend analysis features.

#### Out of Scope:
- Advanced AI-driven forecasting capabilities.
- Development of a mobile application.

### 4. Requirements

#### Functional Requirements:
1. **Real-time Inventory Tracking:**
   - Capability to monitor stock levels in real-time.
   - Dashboard displaying current stock status and historical data.

2. **Automated Restocking Alerts:**
   - System to send notifications when stock levels fall below predefined thresholds.
   - Customizable alert settings for different product categories.

3. **Sales Trend Analysis:**
   - Tools to analyze past sales data and predict future trends.
   - Reports and visualizations to assist in decision-making.

#### Non-Functional Requirements:
1. **Performance:**
   - System should handle concurrent users without performance degradation.
   - Real-time updates should reflect within 5 seconds of a change in stock levels.

2. **Scalability:**
   - Ability to scale horizontally to accommodate increasing data and user load.
   - Modular architecture to add new features without major overhauls.

3. **Security:**
   - Role-based access control to restrict data access based on user roles.
   - Encrypted data storage to protect sensitive information.

4. **Integration:**
   - Seamless integration with existing ERP systems.
   - API support for third-party applications to access inventory data.

5. **Compatibility:**
   - Cross-browser compatibility for the web application.
   - Responsive design to ensure usability on various devices.

#### Technical Environment:
- **Preferred Platform:** Web-based application.
- **Preferred Programming Language:** Python, Flask, PostgreSQL, React.
- **Database Requirements:** PostgreSQL.
- **Deployment Preferences:** AWS Cloud hosting.

#### User Interface Requirements:
- Minimalistic dashboard with easy navigation.
- Intuitive design to facilitate quick access to key functionalities.

#### Known Constraints:
- Budget limitations for advanced analytics.
- Internet dependency for real-time tracking.

#### Competitors/References:
- Coca-Cola’s retail inventory solutions.
- Unilever’s supply chain tools.

### 5. API Endpoints

To support the functional requirements of the Retail Inventory Management System, the following API endpoints are proposed:

#### 1. Inventory Management

- **GET /api/inventory**
  - **Purpose:** Retrieve the current stock levels for all products.
  - **Inputs:** Optional query parameters for filtering by product category or location.
  - **Outputs:** JSON object containing product IDs, names, and stock levels.
  - **Errors/Exceptions:** 404 if no products found, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 100 requests per minute.
  - **Response Time:** < 2 seconds.

- **POST /api/inventory**
  - **Purpose:** Add a new product to the inventory.
  - **Inputs:** JSON object with product details (name, category, initial stock level).
  - **Outputs:** Confirmation message with product ID.
  - **Errors/Exceptions:** 400 for invalid input, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 50 requests per minute.
  - **Response Time:** < 3 seconds.

- **PUT /api/inventory/{productId}**
  - **Purpose:** Update stock levels for a specific product.
  - **Inputs:** JSON object with updated stock level.
  - **Outputs:** Confirmation message.
  - **Errors/Exceptions:** 404 if product not found, 400 for invalid input, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 50 requests per minute.
  - **Response Time:** < 3 seconds.

- **DELETE /api/inventory/{productId}**
  - **Purpose:** Remove a product from the inventory.
  - **Inputs:** Product ID in the URL path.
  - **Outputs:** Confirmation message.
  - **Errors/Exceptions:** 404 if product not found, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 20 requests per minute.
  - **Response Time:** < 3 seconds.

#### 2. Restocking Alerts

- **GET /api/alerts**
  - **Purpose:** Retrieve all active restocking alerts.
  - **Inputs:** Optional query parameters for filtering by product category.
  - **Outputs:** JSON object containing alert details.
  - **Errors/Exceptions:** 404 if no alerts found, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 100 requests per minute.
  - **Response Time:** < 2 seconds.

- **POST /api/alerts**
  - **Purpose:** Create a new restocking alert.
  - **Inputs:** JSON object with alert details (product ID, threshold level).
  - **Outputs:** Confirmation message with alert ID.
  - **Errors/Exceptions:** 400 for invalid input, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 50 requests per minute.
  - **Response Time:** < 3 seconds.

- **DELETE /api/alerts/{alertId}**
  - **Purpose:** Remove a restocking alert.
  - **Inputs:** Alert ID in the URL path.
  - **Outputs:** Confirmation message.
  - **Errors/Exceptions:** 404 if alert not found, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 20 requests per minute.
  - **Response Time:** < 3 seconds.

#### 3. Sales Trend Analysis

- **GET /api/sales/trends**
  - **Purpose:** Retrieve sales trend analysis reports.
  - **Inputs:** Optional query parameters for date range and product category.
  - **Outputs:** JSON object containing sales trends and predictions.
  - **Errors/Exceptions:** 404 if no data found, 500 for server errors.
  - **Authentication:** Required.
  - **Rate Limits:** 100 requests per minute.
  - **Response Time:** < 5 seconds.

### 6. Database Schema

To support the functionality of the Retail Inventory Management System, the following database schema is proposed:

#### Tables and Relationships

1. **Products**
   - **Fields:**
     - `product_id` (Primary Key, Integer, Auto-increment)
     - `name` (String, Not Null)
     - `category` (String, Not Null)
     - `initial_stock_level` (Integer, Not Null)
     - `current_stock_level` (Integer, Not Null)
   - **Indexes:**
     - Index on `category` for quick filtering.

2. **Alerts**
   - **Fields:**
     - `alert_id` (Primary Key, Integer, Auto-increment)
     - `product_id` (Foreign Key, Integer, References Products(product_id))
     - `threshold_level` (Integer, Not Null)
   - **Indexes:**
     - Index on `product_id` for quick lookup.

3. **Sales**
   - **Fields:**
     - `sale_id` (Primary Key, Integer, Auto-increment)
     - `product_id` (Foreign Key, Integer, References Products(product_id))
     - `quantity_sold` (Integer, Not Null)
     - `sale_date` (Date, Not Null)
   - **Indexes:**
     - Index on `sale_date` for trend analysis.

#### Constraints and Triggers

- **Constraints:**
  - Foreign key constraints to ensure referential integrity between `Products`, `Alerts`, and `Sales`.
  - Unique constraint on `name` in `Products` to prevent duplicate entries.

- **Triggers:**
  - Trigger to update `current_stock_level` in `Products` table after each sale is recorded in the `Sales` table.

### 7. Entity-Relationship Diagram (ERD)

Below is a visual representation of the database schema:

```
+-----------------+       +-----------------+       +-----------------+
|    Products     |       |     Alerts      |       |     Sales       |
+-----------------+       +-----------------+       +-----------------+
| product_id (PK) |<----->| alert_id (PK)   |       | sale_id (PK)    |
| name            |       | product_id (FK) |<----->| product_id (FK) |
| category        |       | threshold_level |       | quantity_sold   |
| initial_stock   |       +-----------------+       | sale_date       |
| current_stock   |                                   +-----------------+
+-----------------+
```

### 8. Conclusion
The Retail Inventory Management System is designed to streamline inventory processes, reduce waste, and improve forecasting for retail partners and supply chain teams. By focusing on real-time tracking and automated alerts, the system aims to enhance operational efficiency and decision-making. The project will be developed using a web-based platform with a focus on simplicity and ease of use, leveraging technologies such as Python, Flask, PostgreSQL, and React.