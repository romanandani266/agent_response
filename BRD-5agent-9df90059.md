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

#### Key Features/Functionalities:
- Real-time inventory tracking.
- Automated restocking alerts.
- Sales trend analysis.

#### Technical Requirements:
- **Preferred Platform:** Web-based application.
- **Programming Language:** Python, Flask, PostgreSQL, React.
- **Database:** PostgreSQL.
- **Security:** Role-based access control, encrypted data storage.
- **Deployment Preferences:** AWS Cloud hosting.

#### Functional Requirements:
1. **Real-time Inventory Tracking:**
   - The system must provide real-time updates on stock levels.
   - Users should be able to view current stock levels, historical data, and trends.

2. **Automated Restocking Alerts:**
   - The system should automatically notify users when stock levels fall below a predefined threshold.
   - Alerts should be customizable based on product type and sales velocity.

3. **Sales Trend Analysis:**
   - The system should analyze sales data to identify trends and predict future demand.
   - Users should be able to generate reports on sales trends and inventory turnover.

#### Non-Functional Requirements:
1. **Performance:**
   - The system should handle up to 10,000 concurrent users without performance degradation.
   - Real-time updates should have a latency of no more than 2 seconds.

2. **Scalability:**
   - The system should be scalable to accommodate future growth in data volume and user base.
   - The architecture should support horizontal scaling.

3. **Security:**
   - Implement role-based access control to restrict access to sensitive data.
   - All data should be encrypted both in transit and at rest.

4. **Integration:**
   - The system should integrate with existing ERP systems for seamless data exchange.
   - APIs should be provided for third-party integrations.

#### User Interface Requirements:
- Minimalistic dashboard with easy navigation.
- Responsive design to support various screen sizes.

#### Known Constraints:
- Budget limitations for advanced analytics.
- Internet dependency for real-time tracking.

### 5. Expected Benefits
- Reduction in stock shortages and overstocking.
- Improved supply chain efficiency.
- Enhanced sales forecasting capabilities.

### 6. Primary Deliverables
- A web-based inventory tracking system.
- Automated stock alert notifications.

### 7. Target Audience
- Retail partners.
- PepsiCo supply chain team.
- Warehouse managers.

### 8. Stakeholders
- Retail partners.
- PepsiCo supply chain team.
- Warehouse managers.
- IT development team.

### 9. Assumptions
- The system will be primarily used by retail partners and supply chain teams.
- Internet connectivity is available for real-time tracking.
- Budget constraints will limit the scope of advanced analytics features.

### 10. Competitors/References
- Coca-Cola’s retail inventory solutions.
- Unilever’s supply chain tools.

### 11. Conclusion
The Retail Inventory Management System is designed to streamline inventory processes, reduce waste, and improve forecasting for retail partners and supply chain teams. By focusing on real-time tracking and automated alerts, the system aims to enhance operational efficiency and decision-making capabilities.

### 12. API Endpoints

#### 12.1 Authentication and Authorization
- **POST /api/auth/login**
  - **Purpose:** Authenticate users and provide a JWT token for session management.
  - **Inputs:** JSON object with `username` and `password`.
  - **Outputs:** JWT token if authentication is successful.
  - **Errors/Exceptions:** 401 Unauthorized if credentials are invalid.
  - **Rate Limits:** 5 requests per minute per user.
  - **Response Time:** < 500ms.

- **POST /api/auth/logout**
  - **Purpose:** Invalidate the current user session.
  - **Inputs:** JWT token in the request header.
  - **Outputs:** Success message.
  - **Errors/Exceptions:** 401 Unauthorized if token is invalid.
  - **Rate Limits:** 10 requests per minute per user.
  - **Response Time:** < 300ms.

#### 12.2 Inventory Management
- **GET /api/inventory**
  - **Purpose:** Retrieve real-time inventory data.
  - **Inputs:** Optional query parameters for filtering (e.g., product ID, category).
  - **Outputs:** JSON array of inventory items with current stock levels.
  - **Errors/Exceptions:** 400 Bad Request for invalid parameters.
  - **Rate Limits:** 100 requests per minute per user.
  - **Response Time:** < 1 second.

- **PUT /api/inventory/{productId}**
  - **Purpose:** Update stock levels for a specific product.
  - **Inputs:** JSON object with updated stock level.
  - **Outputs:** Success message with updated inventory data.
  - **Errors/Exceptions:** 404 Not Found if product ID is invalid.
  - **Rate Limits:** 50 requests per minute per user.
  - **Response Time:** < 500ms.

#### 12.3 Restocking Alerts
- **GET /api/alerts**
  - **Purpose:** Retrieve all active restocking alerts.
  - **Inputs:** Optional query parameters for filtering (e.g., product ID).
  - **Outputs:** JSON array of active alerts.
  - **Errors/Exceptions:** 400 Bad Request for invalid parameters.
  - **Rate Limits:** 50 requests per minute per user.
  - **Response Time:** < 1 second.

- **POST /api/alerts**
  - **Purpose:** Create a new restocking alert.
  - **Inputs:** JSON object with alert details (e.g., product ID, threshold).
  - **Outputs:** Success message with alert ID.
  - **Errors/Exceptions:** 400 Bad Request for invalid input data.
  - **Rate Limits:** 20 requests per minute per user.
  - **Response Time:** < 500ms.

- **DELETE /api/alerts/{alertId}**
  - **Purpose:** Delete an existing restocking alert.
  - **Inputs:** Alert ID in the URL path.
  - **Outputs:** Success message.
  - **Errors/Exceptions:** 404 Not Found if alert ID is invalid.
  - **Rate Limits:** 20 requests per minute per user.
  - **Response Time:** < 300ms.

#### 12.4 Sales Trend Analysis
- **GET /api/sales/trends**
  - **Purpose:** Retrieve sales trend analysis data.
  - **Inputs:** Optional query parameters for date range and product filters.
  - **Outputs:** JSON object with sales trends and analysis.
  - **Errors/Exceptions:** 400 Bad Request for invalid parameters.
  - **Rate Limits:** 30 requests per minute per user.
  - **Response Time:** < 2 seconds.

- **POST /api/sales/reports**
  - **Purpose:** Generate a sales report based on specified criteria.
  - **Inputs:** JSON object with report criteria (e.g., date range, product categories).
  - **Outputs:** Downloadable report file.
  - **Errors/Exceptions:** 400 Bad Request for invalid input data.
  - **Rate Limits:** 10 requests per minute per user.
  - **Response Time:** < 5 seconds.

### 13. Security and Compliance

#### Compliance Standards Applicable:
1. **General Data Protection Regulation (GDPR):**
   - **Compliance Requirements:**
     - Data minimization and purpose limitation.
     - Obtain explicit consent for data processing.
     - Right to access, rectify, and erase personal data.
     - Data breach notification within 72 hours.
   - **System Measures:**
     - Implement consent management for data collection.
     - Provide user interfaces for data access and deletion requests.
     - Regular audits and data protection impact assessments.
     - Encryption and pseudonymization of personal data.

2. **Payment Card Industry Data Security Standard (PCI-DSS):**
   - **Compliance Requirements:**
     - Secure storage of cardholder data.
     - Maintain a secure network and systems.
     - Implement strong access control measures.
     - Regularly monitor and test networks.
   - **System Measures:**
     - Use of tokenization for card data.
     - Firewalls and intrusion detection systems.
     - Role-based access control and logging.
     - Regular vulnerability assessments and penetration testing.

#### Security Measures:
- All endpoints require JWT token authentication.
- Role-based access control to ensure users can only access data relevant to their role.
- Data encryption in transit and at rest to comply with industry standards.

#### Data Privacy Rules:
- Implement data anonymization and pseudonymization techniques.
- Ensure data processing activities are documented and transparent.
- Provide mechanisms for users to exercise their data rights.

#### Audit Controls:
- Maintain logs of all access and data modification activities.
- Conduct regular security audits and compliance checks.
- Implement automated alerts for suspicious activities.

#### Compliance Validation:
- **During Implementation:**
  - Conduct a Data Protection Impact Assessment (DPIA).
  - Review and update privacy policies and terms of service.
  - Perform security testing and vulnerability assessments.

- **Post-Implementation:**
  - Schedule regular compliance audits and reviews.
  - Monitor for changes in regulatory requirements.
  - Update system features and policies as needed to maintain compliance.

### 14. Database Schema

#### Tables and Relationships

1. **Users**
   - **Fields:**
     - `user_id` (Primary Key, Integer, Auto-increment)
     - `username` (Varchar, Unique, Not Null)
     - `password_hash` (Varchar, Not Null)
     - `role` (Varchar, Not Null)
     - `created_at` (Timestamp, Default: Current Timestamp)
   - **Indexes:**
     - Unique index on `username`.

2. **Products**
   - **Fields:**
     - `product_id` (Primary Key, Integer, Auto-increment)
     - `product_name` (Varchar, Not Null)
     - `category` (Varchar, Not Null)
     - `price` (Decimal, Not Null)
     - `created_at` (Timestamp, Default: Current Timestamp)

3. **Inventory**
   - **Fields:**
     - `inventory_id` (Primary Key, Integer, Auto-increment)
     - `product_id` (Foreign Key, Integer, References `Products(product_id)`)
     - `stock_level` (Integer, Not Null)
     - `last_updated` (Timestamp, Default: Current Timestamp)
   - **Indexes:**
     - Index on `product_id`.

4. **Alerts**
   - **Fields:**
     - `alert_id` (Primary Key, Integer, Auto-increment)
     - `product_id` (Foreign Key, Integer, References `Products(product_id)`)
     - `threshold` (Integer, Not Null)
     - `created_at` (Timestamp, Default: Current Timestamp)
   - **Indexes:**
     - Index on `product_id`.

5. **Sales**
   - **Fields:**
     - `sale_id` (Primary Key, Integer, Auto-increment)
     - `product_id` (Foreign Key, Integer, References `Products(product_id)`)
     - `quantity_sold` (Integer, Not Null)
     - `sale_date` (Date, Not Null)
   - **Indexes:**
     - Index on `product_id` and `sale_date`.

#### Entity-Relationship Diagram (ERD)

```plaintext
+----------------+       +----------------+       +----------------+
|     Users      |       |    Products    |       |   Inventory    |
+----------------+       +----------------+       +----------------+
| user_id (PK)   |       | product_id (PK)|       | inventory_id(PK)|
| username       |       | product_name   |       | product_id (FK) |
| password_hash  |       | category       |       | stock_level     |
| role           |       | price          |       | last_updated    |
| created_at     |       | created_at     |       +----------------+
+----------------+       +----------------+
                               |
                               |
                               v
+----------------+       +----------------+       +----------------+
|     Alerts     |       |     Sales      |
+----------------+       +----------------+
| alert_id (PK)  |       | sale_id (PK)   |
| product_id (FK)|       | product_id (FK)|
| threshold      |       | quantity_sold  |
| created_at     |       | sale_date      |
+----------------+       +----------------+
```

#### Constraints and Triggers
- **Constraints:**
  - Foreign key constraints to ensure referential integrity between `Products`, `Inventory`, `Alerts`, and `Sales`.
  - Unique constraint on `Users.username`.

- **Triggers:**
  - Trigger to update `Inventory.last_updated` whenever `stock_level` is modified.
  - Trigger to send notifications when `Inventory.stock_level` falls below the threshold defined in `Alerts`.

This database schema is designed to support the application's functionality while ensuring data integrity and performance.