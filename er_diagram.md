```mermaid
erDiagram
    USERS {
        INTEGER user_id PK
        TEXT username
        TEXT password
        TEXT role
    }
    
    SUPPLIERS {
        INTEGER supplier_id PK
        TEXT supplier_name
        TEXT contact_info
    }

    ITEMS {
        INTEGER item_id PK
        TEXT item_name
        TEXT barcode
        TEXT category
        INTEGER quantity_in_stock
        INTEGER reorder_level
        INTEGER supplier_id FK
    }
    
    STOCKMOVEMENTS {
        INTEGER movement_id PK
        INTEGER item_id FK
        TEXT movement_type
        INTEGER quantity
        DATETIME timestamp
        INTEGER user_id FK
    }

    USERS ||--o{ STOCKMOVEMENTS : "creates"
    ITEMS ||--o{ STOCKMOVEMENTS : "tracks"
    SUPPLIERS ||--o{ ITEMS : "supplies"