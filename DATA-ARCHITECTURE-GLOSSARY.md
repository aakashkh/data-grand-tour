# Data Architecture Glossary for Business Users

*A comprehensive guide to modern data architecture terminology*

---

## **Storage & Schema Models**

### **Schema-on-Read**
**What it means:** Data structure is applied when you query the data, not when you store it.  
**Business impact:** Faster data ingestion, more flexibility to explore data in different ways.  
**Example:** Storing customer feedback as raw text files, then analyzing sentiment when needed.

### **Schema-on-Write**
**What it means:** Data structure is enforced when data is loaded into the system.  
**Business impact:** Consistent, reliable reports but slower to adapt to new data types.  
**Example:** Financial transactions must follow strict format before entering the accounting system.

### **Row-Oriented Storage**
**What it means:** Data is stored record by record (like Excel rows).  
**Business impact:** Fast for individual record lookups and updates.  
**Example:** Customer profile updates, order processing systems.

### **Columnar Storage**
**What it means:** Data is stored column by column (like Excel columns).  
**Business impact:** Much faster for analytics and reporting across large datasets.  
**Example:** Analyzing total sales across millions of transactions.

### **In-Memory Storage**
**What it means:** Data is kept in computer's fast memory (RAM) instead of disk.  
**Business impact:** Ultra-fast queries but higher costs and limited data size.  
**Example:** Real-time fraud detection, live dashboards.

---

## **Processing Patterns**

### **ETL (Extract, Transform, Load)**
**What it means:** Traditional approach - clean and structure data before storing it.  
**Business impact:** High data quality but slower time-to-insight.  
**Example:** Nightly processing of sales data into clean reports.

### **ELT (Extract, Load, Transform)**
**What it means:** Modern approach - store raw data first, clean it when needed.  
**Business impact:** Faster data availability, more flexibility for different analyses.  
**Example:** Loading all customer interactions immediately, analyzing patterns later.

### **Batch Processing**
**What it means:** Processing data in scheduled chunks (hourly, daily, weekly).  
**Business impact:** Cost-effective for large volumes but not real-time.  
**Example:** Monthly financial reports, weekly inventory updates.

### **Stream Processing**
**What it means:** Processing data continuously as it arrives.  
**Business impact:** Real-time insights but higher complexity and cost.  
**Example:** Live website personalization, instant fraud alerts.

---

## **Database Types**

### **OLTP (Online Transaction Processing)**
**What it means:** Systems designed for high-volume, fast individual transactions.  
**Business impact:** Powers day-to-day operations efficiently.  
**Example:** E-commerce checkout, banking transactions, inventory updates.

### **OLAP (Online Analytical Processing)**
**What it means:** Systems designed for complex analysis across large datasets.  
**Business impact:** Enables business intelligence and strategic decision-making.  
**Example:** Sales trend analysis, customer segmentation, financial forecasting.

---

## **Data Architecture Patterns**

### **Data Lake**
**What it means:** Central repository storing all types of raw data at low cost.  
**Business impact:** Flexible, cost-effective storage for future analytics needs.  
**Best for:** Organizations with diverse data types and exploratory analytics needs.

### **Data Warehouse**
**What it means:** Structured repository optimized for business reporting and analytics.  
**Business impact:** Reliable, fast reports but requires upfront planning.  
**Best for:** Organizations with well-defined reporting requirements and compliance needs.

### **Data Lakehouse**
**What it means:** Combines flexibility of data lakes with reliability of data warehouses.  
**Business impact:** Best of both worlds - flexibility and performance.  
**Best for:** Organizations wanting both exploratory analytics and reliable reporting.

### **Data Fabric**
**What it means:** Virtual layer that connects data across different systems without moving it.  
**Business impact:** Instant access to data across the organization without duplication.  
**Best for:** Organizations with data spread across many systems needing real-time access.

### **Data Mesh**
**What it means:** Decentralized approach where business domains own their data as products.  
**Business impact:** Scales with organization size, improves data quality through ownership.  
**Best for:** Large organizations with distinct business domains and mature data teams.

### **Microsoft Fabric**
**What it means:** All-in-one cloud platform combining multiple data services.  
**Business impact:** Simplified management, faster implementation, predictable costs.  
**Best for:** Organizations wanting integrated solution with minimal technical complexity.

---

## **Modern Table Formats**

### **Delta Lake**
**What it means:** Enhanced data lake format with database-like reliability features.  
**Business impact:** Reliable data updates and historical tracking in data lakes.  
**Key benefit:** Can update/delete data reliably, see data changes over time.

### **Apache Iceberg**
**What it means:** Open format that works with multiple analytics engines.  
**Business impact:** Avoid vendor lock-in, use best tools for different tasks.  
**Key benefit:** Freedom to choose different analytics tools without data migration.

### **Apache Hudi**
**What it means:** Format optimized for frequent data updates and real-time processing.  
**Business impact:** Keep data fresh with minimal processing overhead.  
**Key benefit:** Efficient handling of frequently changing data.

---

## **Advanced Concepts**

### **ACID Transactions**
**What it means:** Database properties ensuring data reliability (Atomicity, Consistency, Isolation, Durability).  
**Business impact:** Guarantees data accuracy even during system failures.  
**Example:** Bank transfer either completes fully or not at all - no partial transfers.

### **Data Virtualization**
**What it means:** Access data from multiple sources as if it's in one place, without copying.  
**Business impact:** Real-time access to distributed data without storage costs.  
**Example:** Single customer view combining CRM, billing, and support data.

### **Metadata & Data Catalog**
**What it means:** Searchable inventory of all organizational data assets.  
**Business impact:** Find and understand available data quickly, ensure compliance.  
**Example:** Search for "customer data" and find all relevant datasets with descriptions.

### **Time Travel**
**What it means:** Ability to query data as it existed at any point in the past.  
**Business impact:** Audit trails, debugging, regulatory compliance.  
**Example:** "Show me customer data as it was on December 31st for year-end reporting."

---

## **Streaming & Real-Time**

### **Lambda Architecture**
**What it means:** Separate systems for batch and real-time processing, combined for queries.  
**Business impact:** Both historical analysis and real-time insights.  
**Trade-off:** More complex but handles all use cases.

### **Kappa Architecture**
**What it means:** Single stream processing system handles both real-time and historical data.  
**Business impact:** Simpler architecture, consistent processing logic.  
**Trade-off:** Simpler but may not suit all analytical needs.

### **Event Streaming**
**What it means:** Continuous flow of business events processed in real-time.  
**Business impact:** Immediate response to business events and opportunities.  
**Example:** Instant personalization, real-time inventory updates.

---

## **Optimization Techniques**

### **Medallion Architecture (Bronze-Silver-Gold)**
**What it means:** Three-layer approach to data refinement.  
- **Bronze:** Raw data as received
- **Silver:** Cleaned and validated data  
- **Gold:** Business-ready, aggregated data  
**Business impact:** Clear data quality progression, easier troubleshooting.

### **Z-Ordering**
**What it means:** Physical data organization technique for faster queries.  
**Business impact:** Dramatically faster query performance on large datasets.  
**Example:** Customer analysis queries run 10x faster.

### **Liquid Clustering**
**What it means:** Automatic data organization that adapts to query patterns.  
**Business impact:** Self-optimizing performance without manual tuning.  
**Example:** System automatically optimizes for your most common reports.

### **Compaction**
**What it means:** Background process that merges small files into larger, optimal sizes.  
**Business impact:** Maintains query performance as data grows.  
**Example:** Thousands of small hourly files merged into efficient daily files.

---

## **Governance & Security**

### **Data Lineage**
**What it means:** Track where data comes from and how it's transformed.  
**Business impact:** Understand data trustworthiness, debug issues, ensure compliance.  
**Example:** Trace revenue numbers back to original transaction sources.

### **Row-Level Security**
**What it means:** Control which data rows users can see based on their role.  
**Business impact:** Secure data sharing while maintaining single source of truth.  
**Example:** Sales reps only see their region's customer data.

### **Data Contracts**
**What it means:** Formal agreements about data format, quality, and availability.  
**Business impact:** Reliable data dependencies between teams and systems.  
**Example:** Marketing team guaranteed daily customer data by 9 AM.

---

## **Business Decision Framework**

### **When to Choose Each Architecture:**

**Data Lake** → High data variety, cost-conscious, exploratory analytics  
**Data Warehouse** → Established reporting needs, regulatory requirements  
**Lakehouse** → Want both flexibility and performance  
**Data Fabric** → Need real-time access across many systems  
**Data Mesh** → Large organization, domain expertise, mature data culture  
**Microsoft Fabric** → Want integrated solution, Microsoft ecosystem  

### **Key Questions for Architecture Selection:**
1. **Data Volume:** How much data do you have? (GB, TB, PB)
2. **Data Variety:** How many different data types and sources?
3. **Speed Requirements:** Real-time, hourly, daily, or weekly updates?
4. **Team Size:** How many people will work with the data?
5. **Budget:** What's your cost tolerance for storage and compute?
6. **Compliance:** What regulatory requirements must you meet?
7. **Existing Systems:** What technology investments do you already have?

---

*This glossary serves as a reference for business stakeholders to understand and participate in data architecture discussions. For technical implementation details, consult with your data engineering team.*