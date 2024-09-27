# Nike Shoe Store Entity-Relationship Diagram (ERD)

```mermaid
erDiagram
    PRODUCT {
        integer product_id PK
        string model_name
        string size
        string color
        decimal price
        string category
    }
    
    CUSTOMER {
        integer customer_id PK
        string first_name
        string last_name
        string email
        string phone_number
    }

    SALE {
        integer sale_id PK
        date date
        integer customer_id FK
        integer product_id FK
        integer quantity
        decimal total_amount
    }
    
    INVENTORY {
        integer inventory_id PK
        integer product_id FK
        integer stock_level
    }

    CUSTOMER ||--o{ SALE : makes
    PRODUCT ||--o{ SALE : includes
    PRODUCT ||--|| INVENTORY : tracked_in
```
## Description of Entities and Relationships

1. **PRODUCT**: Represents various models of Nike shoes available in the store. Each product has a unique ID and attributes like name, model, price, size, and color.

2. **CUSTOMER**: Contains information about customers, including their unique ID, name, email, and phone number.

3. **SALE**: Captures transaction records that link customers to the products they purchase. It includes details such as the sale date, quantity, and total price.

4. **INVENTORY**: Tracks the stock levels of each product. It contains a unique ID for inventory records and the current stock level for each product.

### Relationships:

- A **customer** can make multiple **sales**, reflecting repeat purchases.
- Each **sale** includes one **product**, indicating that customers purchase specific shoe models.
- Each **product** is tracked in **inventory**, ensuring the store can manage stock levels effectively.
