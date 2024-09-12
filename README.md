
# Database Schema Documentation

## 1. `member` Table
- **Description**: Stores information about members.
- **Columns**:
  - `member_idx`: Primary key, integer.
  - `member_id`: Member's unique ID.
  - `member_name`: Member's name.
  - `member_grade_idx`: Foreign key linking to `member_grade`.
  - `password_change_date`: Date when the password was last changed.
  - `member_block_yn`: Indicates if the member is blocked (Yes/No).
  - `member_regist_date`: Registration date.
  - `member_use_yn`: Indicates if the member is active (Yes/No).
- **Relationships**:
  - `member_grade`: Links to the `MemberGrade` model.
  - Other relationships: `CcAiSuggestion`, `CcAlarm`, `MemberAgreementItem`, `MemberLog`, `Portfolio`, and others.

## 2. `member_agreement_item` Table
- **Description**: Stores the agreements accepted or rejected by members.
- **Columns**:
  - `member_agreement_item_idx`: Primary key.
  - `member_idx`: Foreign key linking to the `member` table.
  - `agreement_idx`: Foreign key linking to the `agreement` table.
  - `agree_yn`: Agreement status (Yes/No).
  - `member_agreement_item_update_date`: Date when the agreement was updated.
- **Relationships**:
  - `member`: Links to the `member` table.
  - `agreement`: Links to the `agreement` table.

## 3. `member_grade` Table
- **Description**: Stores different grades or levels assigned to members.
- **Columns**:
  - `member_grade_idx`: Primary key.
  - Other grade-related columns.
- **Relationships**:
  - `member`: Links to the `member` table (one-to-many relationship).

## 4. `cms_score_list` Table
- **Description**: Stores scores for various cryptocurrencies.
- **Columns**:
  - `idx`: Primary key, autoincrement.
  - `cc_idx`: Foreign key linking to the `cryptocurrency` table.
  - `cc_name`: Name of the cryptocurrency.
  - `cc_code`: Code of the cryptocurrency.
  - `logo_file_path`: Path to the cryptocurrency logo.
  - `sum_score`: Total score of the cryptocurrency.
- **Purpose**: Stores cryptocurrency scores used for comparison or display.

## 5. `member_fcm_token` Table
- **Description**: Stores Firebase Cloud Messaging (FCM) tokens for members.
- **Columns**:
  - `member_fcm_token_idx`: Primary key.
  - `member_idx`: Foreign key linking to the `member` table.
  - `fcm_token`: FCM token string.
  - `device`: Device information.
  - `member_fcm_token_regist_date`: Date when the FCM token was registered.
  - `member_fcm_token_update_date`: Date when the FCM token was updated.
- **Purpose**: Used to manage device tokens for sending notifications to members.

## 6. `app_alarm` Table
- **Description**: Stores alarms that are generated in the system.
- **Columns**:
  - `app_alarm_idx`: Primary key.
  - `app_alarm_type`: Type of alarm (info, warning, etc.).
  - `app_alarm_subject`: Subject of the alarm.
  - `app_alarm_content`: Alarm message.
  - `app_alarm_count`: Number of occurrences of this alarm.
  - `manager_idx`: Foreign key linking to the `manager` table.
  - `app_alarm_regist_date`: Date when the alarm was created.
  
## 7. `app_alarm_item` Table
- **Description**: Stores individual alarm items triggered for specific members.
- **Columns**:
  - `app_alarm_item_idx`: Primary key.
  - `app_alarm_idx`: Foreign key linking to the `app_alarm` table.
  - `member_idx`: Foreign key linking to the `member` table.
  
## 8. `member_openapi` Table
- **Description**: Stores OpenAPI keys associated with members.
- **Columns**:
  - `member_openapi_idx`: Primary key.
  - `member_idx`: Foreign key linking to the `member` table.
  - `member_openapi_key`: The API key assigned to the member.
  - `member_openapi_regist_date`: Date when the API key was registered.
  - `member_openapi_use_yn`: Indicates if the API key is active (Yes/No).
  
## Relationships Overview:
1. **Member to Grade**: A member is associated with a grade, defined in the `member_grade` table.
2. **Member to Agreements**: Members can have multiple agreement items linked to them in the `member_agreement_item` table.
3. **Cryptocurrency Scores**: Cryptocurrencies are scored in the `cms_score_list` table.
4. **FCM Tokens**: Members have Firebase Cloud Messaging tokens stored in `member_fcm_token`.
5. **App Alarms**: System-wide alarms are stored in `app_alarm`, and members can have specific alarm items in `app_alarm_item`.
6. **OpenAPI Keys**: Members can be assigned API keys for external integration, stored in `member_openapi`.





# API Documentation

## 1. Agency

### GET /api/agency/list

Response Data Types:
- `agency_id`: Integer
- `agency_name`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "agency_id": 1,
    "agency_name": "Agency One",
    "created_at": "2023-01-01T12:00:00Z"
  },
  {
    "agency_id": 2,
    "agency_name": "Agency Two",
    "created_at": "2023-01-05T15:00:00Z"
  }
]
```

### POST /api/agency/create

Request Data Types:
- `agency_name`: String

Request Example:
```json
{
  "agency_name": "New Agency"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `agency_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Agency created successfully",
  "agency_id": 3
}
```

## 2. Agreement

### GET /api/agreement/list

Response Data Types:
- `agreement_id`: Integer
- `title`: String
- `content`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "agreement_id": 1,
    "title": "Agreement One",
    "content": "Content of agreement one",
    "created_at": "2023-01-01T12:00:00Z"
  },
  {
    "agreement_id": 2,
    "title": "Agreement Two",
    "content": "Content of agreement two",
    "created_at": "2023-01-05T15:00:00Z"
  }
]
```

### POST /api/agreement/create

Request Data Types:
- `title`: String
- `content`: String

Request Example:
```json
{
  "title": "New Agreement",
  "content": "Details of the new agreement."
}
```

Response Data Types:
- `status`: String
- `message`: String
- `agreement_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Agreement created successfully",
  "agreement_id": 3
}
```

## 3. Banner

### GET /api/banner/list

Response Data Types:
- `banner_id`: Integer
- `image_url`: String (URL)
- `redirect_url`: String (URL)
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "banner_id": 1,
    "image_url": "https://example.com/banner1.jpg",
    "redirect_url": "https://example.com",
    "created_at": "2023-01-01T12:00:00Z"
  },
  {
    "banner_id": 2,
    "image_url": "https://example.com/banner2.jpg",
    "redirect_url": "https://example.com",
    "created_at": "2023-01-05T15:00:00Z"
  }
]
```

### POST /api/banner/create

Request Data Types:
- `image_url`: String (URL)
- `redirect_url`: String (URL)

Request Example:
```json
{
  "image_url": "https://example.com/new_banner.jpg",
  "redirect_url": "https://example.com/new"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `banner_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Banner created successfully",
  "banner_id": 3
}
```

### DELETE /api/banner/{id}

Response Data Types:
- `status`: String
- `message`: String

Response Example:
```json
{
  "status": "success",
  "message": "Banner deleted successfully"
}
```

## 4. Cryptocurrency (CC)

### GET /api/cc/list

Response Data Types:
- `cc_id`: Integer
- `name`: String
- `symbol`: String
- `price`: Float
- `market_cap`: Float
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "cc_id": 1,
    "name": "Bitcoin",
    "symbol": "BTC",
    "price": 45000.75,
    "market_cap": 850000000000,
    "created_at": "2023-01-01T12:00:00Z"
  },
  {
    "cc_id": 2,
    "name": "Ethereum",
    "symbol": "ETH",
    "price": 3000.45,
    "market_cap": 350000000000,
    "created_at": "2023-01-05T15:00:00Z"
  }
]
```

### POST /api/cc/create

Request Data Types:
- `name`: String
- `symbol`: String
- `price`: Float
- `market_cap`: Float

Request Example:
```json
{
  "name": "Litecoin",
  "symbol": "LTC",
  "price": 150.50,
  "market_cap": 10000000000
}
```

Response Data Types:
- `status`: String
- `message`: String
- `cc_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Cryptocurrency added successfully",
  "cc_id": 3
}
```

### DELETE /api/cc/{id}

Response Data Types:
- `status`: String
- `message`: String

Response Example:
```json
{
  "status": "success",
  "message": "Cryptocurrency deleted successfully"
}
```

## 5. Error Report

### GET /api/error_report/list

Response Data Types:
- `report_id`: Integer
- `error_message`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "report_id": 1,
    "error_message": "Error 404",
    "created_at": "2023-01-01T12:00:00Z"
  },
  {
    "report_id": 2,
    "error_message": "Error 500",
    "created_at": "2023-01-05T15:00:00Z"
  }
]
```

### POST /api/error_report/create

Request Data Types:
- `error_message`: String
- `details`: String

Request Example:
```json
{
  "error_message": "Database connection failed",
  "details": "Detailed error description here"
}
```

Response Data Types:
- `status`: String
- `message`: String

Response Example:
```json
{
  "status": "success",
  "message": "Error report submitted successfully"
}
```

## 6. Login

### POST /api/login

Request Data Types:
- `username`: String
- `password`: String

Request Example:
```json
{
  "username": "user123",
  "password": "password123"
}
```

Response Data Types:
- `status`: String
- `token`: String (JWT token)

Response Example:
```json
{
  "status": "success",
  "token": "jwt_token_here"
}
```


## 7. Exchange

### GET /api/exchange/list

Response Data Types:
- `exchange_id`: Integer
- `name`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "exchange_id": 1,
    "name": "Binance",
    "created_at": "2023-01-01T12:00:00Z"
  },
  {
    "exchange_id": 2,
    "name": "Coinbase",
    "created_at": "2023-01-05T15:00:00Z"
  }
]
```

### POST /api/exchange/create

Request Data Types:
- `name`: String
- `details`: String

Request Example:
```json
{
  "name": "Kraken",
  "details": "Some details about the exchange"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `exchange_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Exchange created successfully",
  "exchange_id": 3
}
```

### DELETE /api/exchange/{id}

Response Data Types:
- `status`: String
- `message`: String

Response Example:
```json
{
  "status": "success",
  "message": "Exchange deleted successfully"
}
```

## 8. FAQ

### GET /api/faq/list

Response Data Types:
- `faq_id`: Integer
- `question`: String
- `answer`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "faq_id": 1,
    "question": "What is cryptocurrency?",
    "answer": "Cryptocurrency is a type of digital asset.",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/faq/create

Request Data Types:
- `question`: String
- `answer`: String

Request Example:
```json
{
  "question": "How do I buy Bitcoin?",
  "answer": "You can buy Bitcoin on exchanges like Binance."
}
```

Response Data Types:
- `status`: String
- `message`: String
- `faq_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "FAQ created successfully",
  "faq_id": 2
}
```

## 9. ICO

### GET /api/ico/list

Response Data Types:
- `ico_id`: Integer
- `name`: String
- `status`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "ico_id": 1,
    "name": "ICO One",
    "status": "active",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/ico/create

Request Data Types:
- `name`: String
- `status`: String

Request Example:
```json
{
  "name": "New ICO",
  "status": "upcoming"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `ico_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "ICO created successfully",
  "ico_id": 2
}
```

## 10. Member

### GET /api/member/list

Response Data Types:
- `member_id`: Integer
- `name`: String
- `email`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "member_id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/member/create

Request Data Types:
- `name`: String
- `email`: String

Request Example:
```json
{
  "name": "Jane Doe",
  "email": "jane@example.com"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `member_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Member created successfully",
  "member_id": 2
}
```

## 11. Membership

### GET /api/membership/list

Response Data Types:
- `membership_id`: Integer
- `plan_name`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "membership_id": 1,
    "plan_name": "Premium",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/membership/create

Request Data Types:
- `plan_name`: String

Request Example:
```json
{
  "plan_name": "Gold"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `membership_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Membership created successfully",
  "membership_id": 2
}
```



## 12. News

### GET /api/news/list

Response Data Types:
- `news_id`: Integer
- `title`: String
- `content`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "news_id": 1,
    "title": "Crypto Market Update",
    "content": "The crypto market is experiencing a surge...",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/news/create

Request Data Types:
- `title`: String
- `content`: String

Request Example:
```json
{
  "title": "New Bitcoin Record",
  "content": "Bitcoin reaches an all-time high..."
}
```

Response Data Types:
- `status`: String
- `message`: String
- `news_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "News created successfully",
  "news_id": 2
}
```

## 13. NFT

### GET /api/nft/list

Response Data Types:
- `nft_id`: Integer
- `name`: String
- `creator`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "nft_id": 1,
    "name": "CryptoPunk #1",
    "creator": "John Doe",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/nft/create

Request Data Types:
- `name`: String
- `creator`: String

Request Example:
```json
{
  "name": "CryptoPunk #2",
  "creator": "Jane Doe"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `nft_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "NFT created successfully",
  "nft_id": 2
}
```

## 14. Portfolio

### GET /api/portfolio/list

Response Data Types:
- `portfolio_id`: Integer
- `name`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "portfolio_id": 1,
    "name": "My Crypto Portfolio",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/portfolio/create

Request Data Types:
- `name`: String

Request Example:
```json
{
  "name": "New Portfolio"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `portfolio_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Portfolio created successfully",
  "portfolio_id": 2
}
```

### DELETE /api/portfolio/delete/{id}

Response Data Types:
- `status`: String
- `message`: String

Response Example:
```json
{
  "status": "success",
  "message": "Portfolio deleted successfully"
}
```

## 15. Privacy

### GET /api/privacy/list

Response Data Types:
- `privacy_id`: Integer
- `policy`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "privacy_id": 1,
    "policy": "We respect your privacy...",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/privacy/create

Request Data Types:
- `policy`: String

Request Example:
```json
{
  "policy": "Our new privacy policy..."
}
```

Response Data Types:
- `status`: String
- `message`: String
- `privacy_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Privacy policy created successfully",
  "privacy_id": 2
}
```

## 16. Q&A

### GET /api/qna/list

Response Data Types:
- `qna_id`: Integer
- `question`: String
- `answer`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "qna_id": 1,
    "question": "How to buy Bitcoin?",
    "answer": "You can buy Bitcoin on exchanges.",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/qna/create

Request Data Types:
- `question`: String
- `answer`: String

Request Example:
```json
{
  "question": "How do I store Bitcoin?",
  "answer": "You can store Bitcoin in a wallet."
}
```

Response Data Types:
- `status`: String
- `message`: String
- `qna_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Q&A created successfully",
  "qna_id": 2
}
```

## 17. Subscription

### GET /api/subscription/list

Response Data Types:
- `subscription_id`: Integer
- `plan`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "subscription_id": 1,
    "plan": "Premium Plan",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/subscription/create

Request Data Types:
- `plan`: String

Request Example:
```json
{
  "plan": "Gold Plan"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `subscription_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Subscription created successfully",
  "subscription_id": 2
}
```

### DELETE /api/subscription/delete/{id}

Response Data Types:
- `status`: String
- `message`: String

Response Example:
```json
{
  "status": "success",
  "message": "Subscription deleted successfully"
}
```

## 18. Terms of Service

### GET /api/terms_of_service/list

Response Data Types:
- `terms_id`: Integer
- `content`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "terms_id": 1,
    "content": "These are the terms of service...",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/terms_of_service/create

Request Data Types:
- `content`: String

Request Example:
```json
{
  "content": "New terms of service..."
}
```

Response Data Types:
- `status`: String
- `message`: String
- `terms_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Terms of service created successfully",
  "terms_id": 2
}
```

## 19. Watchlist

### GET /api/watchlist/list

Response Data Types:
- `watchlist_id`: Integer
- `item_name`: String
- `created_at`: DateTime (ISO 8601)

Response Example:
```json
[
  {
    "watchlist_id": 1,
    "item_name": "Bitcoin",
    "created_at": "2023-01-01T12:00:00Z"
  }
]
```

### POST /api/watchlist/create

Request Data Types:
- `item_name`: String

Request Example:
```json
{
  "item_name": "Ethereum"
}
```

Response Data Types:
- `status`: String
- `message`: String
- `watchlist_id`: Integer

Response Example:
```json
{
  "status": "success",
  "message": "Item added to watchlist",
  "watchlist_id": 2
}
```

### DELETE /api/watchlist/delete/{id}

Response Data Types:
- `status`: String
- `message`: String

Response Example:
```json
{
  "status": "success",
  "message": "Item removed from watchlist"
}
```





