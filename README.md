- 👋 Hi, I’m @QlikDaan
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
QlikDaan/QlikDaan is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
# Entity-Relationship Diagram

```mermaid
%% Description: Entity-Relationship Diagram (ERD) for Trade Item, Bill of Material (BOM), Part, Document, Document Link, Document Type Extension, Inspection Part, Inspection Trade Item, and Accepted Trade Item tables.
%% Author: Daan Koster
%% Created on: 2024-12-07
%% Last Modified: 2024-12-07

erDiagram
    TRADE_ITEM {
        int Trade_Item_ID
        string Trade Item Name
        string Trade Item Type
        int Trade_Item_ID
        int Trade Item Design Part ID
    }

    

    TRADE_ITEM ||--o{ BILL_OF_MATERIAL : "has"
    PART ||--o{ BILL_OF_MATERIAL : "used in"
    TRADE_ITEM ||--o{ DOCUMENT_LINK : "linked to"
    DOCUMENT ||--o{ DOCUMENT_LINK : "linked in"
    DOCUMENT ||--o{ DOCUMENT_TYPE_A : "extended as"
    DOCUMENT ||--o{ DOCUMENT_TYPE_B : "extended as"
    DOCUMENT ||--o{ DOCUMENT_TYPE_C : "extended as"
    PART ||--o{ INSPECTION_PART : "inspected by"
    TRADE_ITEM ||--o{ INSPECTION_TRADE_ITEM : "inspected by"
    TRADE_ITEM ||--o{ ACCEPTED_TRADE_ITEM : "accepted as"
