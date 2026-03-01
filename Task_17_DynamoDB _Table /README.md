DynamoDB Table Creation (Basic)

## Simple Definition
DynamoDB is a **serverless NoSQL database** by AWS. It stores structured data in tables with flexible schema. Unlike relational databases, it uses **Partition Key** and optionally a **Sort Key** for indexing items, allowing fast and scalable access.

---

## Objective
- Learn the basics of **AWS DynamoDB**.
- Create a **NoSQL table** with partition and sort keys.
- Insert and view **sample items**.
- Understand serverless database operations like **Scan** and **Query**.

---

## Steps Performed

### Step 1: Create a Table
- **Table name:** `India`  
- **Partition key:** `state` (String)  
- **Sort key:** `dist` (String)  
- **Capacity mode:** On-demand  
- **Table status:** Active  

### Step 2: Insert Sample Items
- Click **Explore items → Create item → Form editor**.
- Insert sample items:

| state        | dist       | Additional Info |
|-------------|------------|----------------|
| West Bengal | Darjeeling | Population: 1400000, Area: 3700 |
| West Bengal | Kolkata    | Population: 4500000, Area: 185  |
| Bihar       | Patna      | Population: 2100000, Area: 320  |
| Jharkhand   | Jasidih    | (optional)    |

- Click **Save** after each item.

### Step 3: Verify Items
- Click **Explore table items**.
- Confirm that all inserted items are listed.
- Check **Partition Key** and **Sort Key** values.

---

## Proof / Screenshots
1. **Table Details Screenshot**  
   ![Table Details](screenshot1.png)  

2. **Items in Table Screenshot**  
   ![Items Added](screenshot2.png)  

---

## Notes / Tips
- Use **Scan** or **Query** to fetch table data.
- On-demand capacity automatically scales with traffic.
- Enable **Deletion Protection** to prevent accidental deletion.
- DynamoDB is **highly available and serverless**—no infrastructure management required.
