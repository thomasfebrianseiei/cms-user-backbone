
# Cryptocurrency and Related Models Documentation

## Cc (Cryptocurrency)

- **Table name:** `cryptocurrency`
- **Fields:**
  - `cc_idx`: Integer (Primary key)
  - `cmc_idx`: Integer
  - `cc_status_common_code`: String
  - `cc_name`: String
  - `cc_code`: String
  - `cc_slug`: String
  - `logo_file_path`: String
  - `whitepaper_url`: String
  - `whitepaper_file_path`: String
  - `platform`: String
  - `site_url`: String
  - `cc_summary`: String
  - `related_services_yn`: String
  - `max_supply`: String
  - `listing_date`: Date
  - `cc_regist_date`: DateTime (default `utcnow()`)
  - `cc_update_date`: DateTime
  - `cc_use_yn`: String (default 'Y')

- **Relationships:**
  - `cc_ai_suggestion`: One-to-Many (relationship to `CcAiSuggestion`)
  - `cc_alarm`: One-to-Many (relationship to `CcAlarm`)
  - `cc_community`: One-to-Many (relationship to `CcCommunity`)
  - `cc_development`: One-to-Many (relationship to `CcDevelopment`)
  - `cc_tag_item`: One-to-Many (relationship to `CcTagItem`)
  - `cc_watchlist_item`: One-to-Many (relationship to `CcWatchlistItem`)
  - `cc_market_share`: One-to-Many (relationship to `CcMarketShare`)
  - `currency`: One-to-Many (relationship to `Currency`)
  - `ico`: One-to-Many (relationship to `Ico`)
  - `ico_alarm`: One-to-Many (relationship to `IcoAlarm`)
  - `cc_day_trade`: One-to-Many (relationship to `CcDayTrade`)
  - `cc_link_item`: One-to-Many (relationship to `CcLinkItem`)
  - `ai_anomaly_detection`: One-to-Many (relationship to `AiAnomalyDetection`)
  - `ai_candlestick_prediction`: One-to-Many (relationship to `AiCandlestickPrediction`)
  - `ai_price_data`: One-to-Many (relationship to `AiPriceData`)
  - `ai_valuation`: One-to-Many (relationship to `AiValuation`)
  - `news_item`: One-to-Many (relationship to `NewsItem`)
  - `pair`: One-to-Many (relationship to `Pair`)
  - `contributor`: One-to-Many (relationship to `Contributor`)
  - `portfolio_item`: One-to-Many (relationship to `PortfolioItem`)

## CcAiSuggestion

- **Table name:** `cryptocurrency_ai_suggestion`
- **Fields:**
  - `cc_ai_suggestion_idx`: Integer (Primary key)
  - `member_idx`: Integer (Foreign key to `member`)
  - `cc_idx`: Integer (Foreign key to `cryptocurrency`)
  - `column4`: String
  - `column5`: String
  - `column6`: String

- **Relationships:**
  - `cc`: Many-to-One (relationship to `Cc`)
  - `member`: Many-to-One (relationship to `Member`)

## CcAlarm

- **Table name:** `cryptocurrency_alarm`
- **Fields:**
  - `cc_alarm_idx`: Integer (Primary key)
  - `member_idx`: Integer (Foreign key to `member`)
  - `cc_idx`: Integer (Foreign key to `cryptocurrency`)
  - `cc_alarm_market_price`: Numeric
  - `cc_alarm_date`: DateTime
  - `cc_alarm_regist_date`: DateTime (default `utcnow()`)
  - `cc_alarm_update_date`: DateTime
  - `cc_alarm_use_yn`: String (default 'Y')

- **Relationships:**
  - `cc`: Many-to-One (relationship to `Cc`)
  - `member`: Many-to-One (relationship to `Member`)

## CcCommunity

- **Table name:** `cryptocurrency_community`
- **Fields:**
  - `cc_community_idx`: Integer (Primary key)
  - `cc_idx`: Integer (Foreign key to `cryptocurrency`)
  - `facebook_likes`: Integer
  - `twitter_followers`: Integer
  - `reddit_average_posts_48h`: Numeric
  - `reddit_average_comments_48h`: Numeric
  - `reddit_subscribers`: Integer
  - `reddit_accounts_active_48h`: Numeric
  - `telegram_channel_user_count`: Numeric
  - `cc_community_regist_date`: DateTime (default `utcnow()`)
  - `cc_community_update_date`: DateTime

- **Relationships:**
  - `cc`: Many-to-One (relationship to `Cc`)

## CcDevelopment

- **Table name:** `cryptocurrency_development`
- **Fields:**
  - `cc_development_idx`: Integer (Primary key)
  - `cc_idx`: Integer (Foreign key to `cryptocurrency`)
  - `fork_count`: Integer
  - `star_count`: Integer
  - `subscriber_count`: Integer
  - `total_issue_count`: Integer
  - `closed_issue_count`: Integer
  - `pull_request_merged_count`: Integer
  - `pull_request_contributors_count`: Integer
  - `code_addition_4_weeks_count`: Integer
  - `code_deletion_4_weeks_count`: Integer
  - `commit_4_weeks_count`: Integer
  - `cc_development_regist_date`: DateTime (default `utcnow()`)
  - `cc_development_update_date`: DateTime

- **Relationships:**
  - `cc`: Many-to-One (relationship to `Cc`)

## CcTagItem

- **Table name:** `cryptocurrency_tag_item`
- **Fields:**
  - `cc_tag_item_idx`: Integer (Primary key)
  - `cc_idx`: Integer (Foreign key to `cryptocurrency`)
  - `tag_idx`: Integer (Foreign key to `tag`)
  - `cc_tag_item_regist_date`: DateTime (default `utcnow()`)
  - `cc_tag_item_update_date`: DateTime
  - `cc_tag_item_use_yn`: String (default 'Y')

- **Relationships:**
  - `cc`: Many-to-One (relationship to `Cc`)
  - `tag`: Many-to-One (relationship to `Tag`)



# Additional Models Documentation

## Language

- **Table name:** `language`
- **Fields:**
  - `language_idx`: Integer (Primary key)
  - `language_name`: String
  - `language_notation`: String
  - `language_regist_date`: DateTime (default `utcnow()`)
  - `language_update_date`: DateTime
  - `language_use_yn`: String (default 'Y')

## SpatialRefSys

- **Table name:** `spatial_ref_sys`
- **Fields:**
  - `srid`: Integer (Primary key)
  - `auth_name`: String
  - `auth_srid`: Integer
  - `srtext`: String
  - `proj4text`: String

## TimeCommonCode

- **Table name:** `time_common_code`
- **Fields:**
  - `time_code_idx`: Integer (Primary key)
  - `time`: String
  - `time_code`: Integer

## CommonCode

- **Table name:** `common_code`
- **Fields:**
  - `common_code_idx`: Integer (Primary key)
  - `code`: String
  - `name`: String
  - `parent_code`: String
  - `note`: String
  - `common_code_regist_date`: DateTime (default `utcnow()`)
  - `common_code_update_date`: DateTime
  - `common_code_use_yn`: String (default 'Y')

## Subscription

- **Table name:** `subscription`
- **Fields:**
  - `subscription_idx`: Integer (Primary key)
  - `member_idx`: Integer (Foreign key to `member`)
  - `subscription_name`: String
  - `subscription_email`: String
  - `subscription_regist_date`: DateTime (default `utcnow()`)
  - `subscription_update_date`: DateTime
  - `subscription_use_yn`: String (default 'Y')

- **Relationships:**
  - `member`: Many-to-One (relationship to `Member`)

## NewsLetter

- **Table name:** `news_letter`
- **Fields:**
  - `news_letter_idx`: Integer (Primary key)
  - `news_letter_subject`: String
  - `news_letter_content`: String
  - `news_letter_regist_date`: DateTime (default `utcnow()`)
  - `news_letter_count`: Integer
  - `member_idx_list`: String

## ErrorLog

- **Table name:** `error_log`
- **Fields:**
  - `error_log_idx`: Integer (Primary key)
  - `error_log_type`: String
  - `error_log_content1`: String
  - `error_log_content2`: String
  - `error_log_content3`: String
  - `error_log_actual_date`: DateTime (default `utcnow()`)



# NFT Models Documentation

## NftCollection

- **Table name:** `nft_collection`
- **Fields:**
  - `nft_collection_idx`: Integer (Primary key)
  - `nft_collection_name`: String
  - `nft_collection_logo_file_path`: String
  - `nft_collection_link`: String
  - `nft_collection_total_assets`: Integer
  - `nft_collection_regist_date`: DateTime (default `utcnow()`)
  - `nft_collection_update_date`: DateTime
  - `nft_collection_use_yn`: String (default 'Y')
  - `nft_collection_slug_name`: String

- **Relationships:**
  - `nft_collection_price`: One-to-Many (relationship to `NftCollectionPrice`)

## NftCollectionPrice

- **Table name:** `nft_collection_price`
- **Fields:**
  - `nft_collection_price_idx`: Integer (Primary key)
  - `nft_collection_idx`: Integer (Foreign key to `nft_collection`)
  - `nft_collection_price_market_cap`: Numeric
  - `nft_collection_price_week_volume`: Numeric
  - `nft_collection_price_week_sales`: Numeric
  - `nft_collection_price_regist_date`: DateTime (default `utcnow()`)
  - `nft_collection_price_total_volume`: Numeric
  - `nft_collection_price_day_volume`: Numeric
  - `nft_collection_price_floor_price`: Numeric

- **Relationships:**
  - `nft_collection`: Many-to-One (relationship to `NftCollection`)







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





