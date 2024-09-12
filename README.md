
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

## 1. Get Member Information
- **Endpoint**: `GET /api/members/{member_idx}`
- **Description**: Fetch a member's detailed information by `member_idx`.

### Example Request:
```
GET /api/members/1
```

### Example Response:
```json
{
  "member_idx": 1,
  "member_id": "john_doe",
  "member_name": "John Doe",
  "member_grade": "Premium",
  "member_regist_date": "2023-01-15T12:34:56Z",
  "member_use_yn": "Y"
}
```

## 2. Create Member
- **Endpoint**: `POST /api/members`
- **Description**: Create a new member.

### Example Request:
```
POST /api/members
Content-Type: application/json

{
  "member_id": "jane_doe",
  "member_name": "Jane Doe",
  "member_grade_idx": 2,
  "password": "password123"
}
```

### Example Response:
```json
{
  "member_idx": 2,
  "member_id": "jane_doe",
  "member_name": "Jane Doe",
  "member_grade": "Basic",
  "member_regist_date": "2024-09-11T09:21:34Z"
}
```

## 3. Update Member
- **Endpoint**: `PUT /api/members/{member_idx}`
- **Description**: Update details for a specific member.

### Example Request:
```
PUT /api/members/2
Content-Type: application/json

{
  "member_name": "Jane Doe Updated",
  "member_grade_idx": 3
}
```

### Example Response:
```json
{
  "member_idx": 2,
  "member_id": "jane_doe",
  "member_name": "Jane Doe Updated",
  "member_grade": "VIP",
  "member_update_date": "2024-09-11T12:21:34Z"
}
```

## 4. Delete Member
- **Endpoint**: `DELETE /api/members/{member_idx}`
- **Description**: Delete a member.

### Example Request:
```
DELETE /api/members/2
```

### Example Response:
```json
{
  "message": "Member deleted successfully"
}
```

## 5. Get Member Agreements
- **Endpoint**: `GET /api/members/{member_idx}/agreements`
- **Description**: Fetch all agreement items for a specific member.

### Example Request:
```
GET /api/members/1/agreements
```

### Example Response:
```json
[
  {
    "agreement_idx": 1,
    "agree_yn": "Y",
    "member_agreement_item_update_date": "2023-01-10T10:00:00Z"
  },
  {
    "agreement_idx": 2,
    "agree_yn": "N",
    "member_agreement_item_update_date": "2023-01-11T11:00:00Z"
  }
]
```

## 6. Add Agreement for Member
- **Endpoint**: `POST /api/members/{member_idx}/agreements`
- **Description**: Add an agreement item for a member.

### Example Request:
```
POST /api/members/1/agreements
Content-Type: application/json

{
  "agreement_idx": 3,
  "agree_yn": "Y"
}
```

### Example Response:
```json
{
  "member_agreement_item_idx": 4,
  "agreement_idx": 3,
  "member_idx": 1,
  "agree_yn": "Y",
  "member_agreement_item_update_date": "2024-09-11T14:21:34Z"
}
```

## 7. Get Cryptocurrency Scores
- **Endpoint**: `GET /api/cryptocurrencies/scores`
- **Description**: Fetch all cryptocurrency scores.

### Example Request:
```
GET /api/cryptocurrencies/scores
```

### Example Response:
```json
[
  {
    "cc_idx": 1,
    "cc_name": "Bitcoin",
    "cc_code": "BTC",
    "logo_file_path": "/path/to/bitcoin/logo.png",
    "sum_score": 95.0
  },
  {
    "cc_idx": 2,
    "cc_name": "Ethereum",
    "cc_code": "ETH",
    "logo_file_path": "/path/to/ethereum/logo.png",
    "sum_score": 89.5
  }
]
```

## 8. Update Cryptocurrency Score
- **Endpoint**: `PUT /api/cryptocurrencies/scores/{cc_idx}`
- **Description**: Update the score for a cryptocurrency.

### Example Request:
```
PUT /api/cryptocurrencies/scores/1
Content-Type: application/json

{
  "sum_score": 96.0
}
```

### Example Response:
```json
{
  "cc_idx": 1,
  "cc_name": "Bitcoin",
  "sum_score": 96.0,
  "cc_update_date": "2024-09-11T15:21:34Z"
}
```

## 9. Manage Firebase Cloud Messaging (FCM) Tokens
- **Endpoint**: `POST /api/members/{member_idx}/fcm-token`
- **Description**: Register or update an FCM token for a member.

### Example Request:
```
POST /api/members/1/fcm-token
Content-Type: application/json

{
  "fcm_token": "new_token_value",
  "device": "Android"
}
```

### Example Response:
```json
{
  "member_fcm_token_idx": 3,
  "fcm_token": "new_token_value",
  "device": "Android",
  "member_fcm_token_regist_date": "2024-09-11T16:21:34Z"
}
```

## 10. Trigger App Alarm
- **Endpoint**: `POST /api/alarms`
- **Description**: Create a new app alarm.

### Example Request:
```
POST /api/alarms
Content-Type: application/json

{
  "app_alarm_type": "warning",
  "app_alarm_subject": "Low Balance",
  "app_alarm_content": "Your balance is below the minimum limit.",
  "manager_idx": 1
}
```

### Example Response:
```json
{
  "app_alarm_idx": 5,
  "app_alarm_type": "warning",
  "app_alarm_subject": "Low Balance",
  "app_alarm_content": "Your balance is below the minimum limit.",
  "app_alarm_regist_date": "2024-09-11T17:21:34Z"
}
```

## Additional APIs
1. **Get All Members**: `GET /api/members`
2. **Get All App Alarms**: `GET /api/alarms`
3. **Delete App Alarm**: `DELETE /api/alarms/{app_alarm_idx}`
4. **Get Single Cryptocurrency Score**: `GET /api/cryptocurrencies/scores/{cc_idx}`
5. **Delete Cryptocurrency Score**: `DELETE /api/cryptocurrencies/scores/{cc_idx}`
6. **Manage OpenAPI Keys**: `POST /api/members/{member_idx}/openapi-key`
7. **Delete OpenAPI Key**: `DELETE /api/members/{member_idx}/openapi-key/{member_openapi_idx}`
