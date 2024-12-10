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
        int "Trade_Item_ID"
        string "Trade Item Name"
        string "Trade Item Type"
        int "%Trade_Item_ID"  %% Adjusted Key Column
        int "Trade Item Design Part ID"
    }

    BILL_OF_MATERIAL {
        int "BOM ID"
        int "BOM Trade Item ID"
        int "BOM Part ID"
        int "BOM Quantity"
        int "%BOM_ID"  %% Adjusted Key Column
        int "%BOM_Trade_Item_ID"  %% Adjusted Key Column
        int "%BOM_Part_ID"  %% Adjusted Key Column
        int "BOM Design Part ID"
    }

    PART {
        int "Part ID"
        string "Part Name"
        string "Part Type"
        int "%Part_ID"  %% Adjusted Key Column
    }
    
    DOCUMENT {
        int "Document ID"
        string "Document Name"
        string "Document Type"
        int "%Document_ID"  %% Adjusted Key Column
    }
    
    DOCUMENT_LINK {
        int "DL ID"
        int "DL Trade Item ID"
        int "DL Document ID"
        int "%DL_ID"  %% Adjusted Key Column
        int "%DL_Trade_Item_ID"  %% Adjusted Key Column
        int "%DL_Document_ID"  %% Adjusted Key Column
    }
    
    DOCUMENT_TYPE_A {
        int "DTA ID"
        string "DTA Specific Field 1"
        string "DTA Specific Field 2"
        int "%DTA_ID"  %% Adjusted Key Column
    }
    
    DOCUMENT_TYPE_B {
        int "DTB ID"
        string "DTB Specific Field 1"
        string "DTB Specific Field 2"
        int "%DTB_ID"  %% Adjusted Key Column
    }

    DOCUMENT_TYPE_C {
        int "DTC ID"
        string "DTC Specific Field 1"
        string "DTC Specific Field 2"
        int "%DTC_ID"  %% Adjusted Key Column
    }

    INSPECTION_PART {
        int "Inspection Part ID"
        int "Inspection Part Part ID"
        string "Inspection Part Inspection Result"
        date "Inspection Part Inspection Date"
        date "Inspection Part Start Date"
        date "Inspection Part End Date"
        int "%Inspection_Part_ID"  %% Adjusted Key Column
        int "%Inspection_Part_Part_ID"  %% Adjusted Key Column
    }

    INSPECTION_TRADE_ITEM {
        int "ITI ID"
        int "ITI Trade Item ID"
        string "ITI Inspection Result"
        date "ITI Inspection Date"
        date "ITI Start Date"
        date "ITI End Date"
        int "%ITI_ID"  %% Adjusted Key Column
        int "%ITI_Trade_Item_ID"  %% Adjusted Key Column
    }

    ACCEPTED_TRADE_ITEM {
        int "ATI ID"
        int "ATI Trade Item ID"
        date "ATI Acceptance Date"
        int "%ATI_ID"  %% Adjusted Key Column
        int "%ATI_Trade_Item_ID"  %% Adjusted Key Column
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
