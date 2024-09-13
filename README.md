# CMS User Related Models Documentation

![postgres - public](https://github.com/user-attachments/assets/f97e3061-4e45-4e78-91e7-d4b8e4601d24)

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


# Database Documentation

---

## `Tag`
- **Table Name**: `tag`
- **Columns**:
  - `tag_idx`: `Integer`, Primary Key
  - `tag_name`: `String`
  - `tag_summary`: `String`
  - `tag_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `tag_update_date`: `DateTime`
  - `tag_use_yn`: `String`, Default: `'Y'`
  - `tag_code`: `String`
  - `tag_group`: `String`

---

## `CcWatchlist`
- **Table Name**: `cryptocurrency_watchlist`
- **Columns**:
  - `cc_watchlist_idx`: `Integer`, Primary Key
  - `cc_watchlist_name`: `String`
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `cc_watchlist_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cc_watchlist_update_date`: `DateTime`
  - `cc_watchlist_use_yn`: `String`, Default: `'Y'`
  - `cc_watchlist_main_yn`: `String`
  - `cc_watchlist_share_yn`: `String`, Default: `'N'`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, ForeignKey: `member.member_idx`

---

## `CcWatchlistItem`
- **Table Name**: `cryptocurrency_watchlist_item`
- **Columns**:
  - `cc_watchlist_item_idx`: `Integer`, Primary Key
  - `cc_watchlist_idx`: `Integer`
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `cc_watchlist_item_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cc_watchlist_item_update_date`: `DateTime`
  - `cc_watchlist_item_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `cc_watchlist_item`

---

## `CcConvert`
- **Table Name**: `cryptocurrency_convert`
- **Columns**:
  - `cc_convert_idx`: `Integer`, Primary Key
  - `from_cmc_idx`: `Integer`
  - `to_cmc_idx`: `Integer`
  - `member_idx`: `Integer`
  - `from_price`: `Numeric`
  - `to_price`: `Numeric`
  - `cc_convert_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cc_convert_update_date`: `DateTime`
  - `cc_convert_predict_date`: `DateTime`
  - `cc_convert_use_yn`: `String`, Default: `'Y'`
  - `exchange_rate`: `Numeric`

---

## `CcMarketShare`
- **Table Name**: `cryptocurrency_market_share`
- **Columns**:
  - `cc_market_share_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `market_share`: `Numeric`
  - `market_price`: `Numeric`
  - `day_price_variance`: `Numeric`
  - `week_price_variance`: `Numeric`
  - `market_cap`: `Numeric`
  - `day_trading_volume`: `Numeric`
  - `circulation_supply`: `Numeric`
  - `cc_market_share_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cc_market_share_update_date`: `DateTime`
  - `market_share_date`: `Date`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `cc_market_share`

---

## `Currency`
- **Table Name**: `currency`
- **Columns**:
  - `currency_idx`: `Integer`, Primary Key
  - `currency_logo_file_path`: `String`
  - `country`: `String`
  - `currency_name`: `String`
  - `currency_code`: `String`
  - `currency_symbol`: `String`
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `currency_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `currency_update_date`: `DateTime`
  - `currency_use_yn`: `String`, Default: `'Y'`
  - `cmc_idx`: `Integer`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `currency`
  - `currency_rate`: One-to-Many relationship with `CurrencyRate`, back_populates: `currency`
  - `exchange_currency_item`: One-to-Many relationship with `ExchangeCurrencyItem`, back_populates: `currency`

---

## `CurrencyRate`
- **Table Name**: `currency_rate`
- **Columns**:
  - `currency_rate_idx`: `Integer`, Primary Key
  - `currency_idx`: `Integer`, ForeignKey: `currency.currency_idx`
  - `usd_rate`: `Numeric`
  - `currency_rate_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `round_count`: `Integer`

- **Relationships**:
  - `currency`: Many-to-One relationship with `Currency`, back_populates: `currency_rate`

---

## `Ico`
- **Table Name**: `ico`
- **Columns**:
  - `ico_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `ico_type_common_code`: `String`
  - `approved_yn`: `String`, Default: `'Y'`
  - `sale_start_date`: `DateTime`
  - `sale_end_date`: `DateTime`
  - `contract_platform`: `String`
  - `category`: `String`
  - `location`: `String`
  - `token_price`: `Numeric`
  - `token_for_sale`: `String`
  - `min_purchase`: `Numeric`
  - `max_purchase`: `Numeric`
  - `token_type`: `String`
  - `soft_cap`: `Numeric`
  - `hard_cap`: `Numeric`
  - `token_currency`: `String`
  - `cap_currency`: `String`
  - `ico_summary`: `String`
  - `ico_detailed_description`: `String`
  - `video_file_path`: `String`
  - `presale_yn`: `String`, Default: `'Y'`
  - `region_participation_restrictions`: `String`
  - `accepting_currency`: `String`
  - `bonus_yn`: `String`, Default: `'Y'`
  - `kyc_yn`: `String`, Default: `'Y'`
  - `airdrop_yn`: `String`, Default: `'Y'`
  - `bounty_yn`: `String`, Default: `'Y'`
  - `whitelist_open_yn`: `String`, Default: `'Y'`
  - `contract_addresses`: `String`
  - `company_name`: `String`
  - `company_address`: `String`
  - `company_email`: `String`
  - `applicant_name`: `String`
  - `applicant_position`: `String`
  - `applicant_email`: `String`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `ico`
  - `ico_raised_amount`: One-to-Many relationship with `IcoRaisedAmount`, back_populates: `ico`
  - `ai_valuation_ico`: One-to-Many relationship with `AiValuationIco`, back_populates: `ico`

---

## `IcoAlarm`
- **Table Name**: `ico_alarm`
- **Columns**:
  - `ico_alarm_idx`: `Integer`, Primary Key
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `ico_alarm_price_or_date`: `String`
  - `ico_alarm_target_raised_amount_rate`: `String`
  - `ico_alarm_date`: `DateTime`
  - `ico_alarm_note`: `String`
  - `ico_alarm_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `ico_alarm_update_date`: `DateTime`
  - `ico_alarm_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, back_populates: `ico_alarm`
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `ico_alarm`

---

## `IcoRaisedAmount`
- **Table Name**: `ico_raised_amount`
- **Columns**:
  - `ico_raised_amount_idx`: `Integer`, Primary Key
  - `ico_idx`: `Integer`, ForeignKey: `ico.ico_idx`
  - `fund_raised`: `Numeric`
  - `ico_raised_amount_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `ico_raised_amount_update_date`: `DateTime`
  - `ico_raised_amount_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `ico`: Many-to-One relationship with `Ico`, back_populates: `

---

## `CcPrice`
- **Table Name**: `cryptocurrency_price`
- **Columns**:
  - `cc_price_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `market_price`: `Numeric`
  - `market_cap`: `Numeric`
  - `cc_market_cap`: `Numeric`
  - `fully_diluted_market_cap`: `Numeric`
  - `cmc_rank`: `Integer`
  - `hour_price_variance`: `Numeric`
  - `hour_trading_volume`: `Numeric`
  - `day_price_variance`: `Numeric`
  - `day_trading_volume`: `Numeric`
  - `day_trading_volume_variance`: `Numeric`
  - `day_cc_trading_volume`: `Numeric`
  - `week_price_variance`: `Numeric`
  - `week_trading_volume`: `Numeric`
  - `dominance`: `Numeric`
  - `cc_price_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cmc_idx`: `Integer`
  - `total_supply`: `String`
  - `circulation_supply`: `String`
  - `round_count`: `Integer`
  - `time_code`: `Integer`

---

## `CcDayTrade`
- **Table Name**: `cryptocurrency_day_trade`
- **Columns**:
  - `cc_day_trade_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `day_trade_date`: `Date`
  - `day_market_price`: `Numeric`
  - `day_high_price`: `Numeric`
  - `day_low_price`: `Numeric`
  - `day_closing_price`: `Numeric`
  - `day_trading_volume`: `Numeric`
  - `day_market_cap`: `Numeric`
  - `cc_day_trade_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cmc_idx`: `Integer`
  - `round_count`: `Integer`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `cc_day_trade`

---

## `CcLatestInfo`
- **Table Name**: `cryptocurrency_latest_info`
- **Columns**:
  - `cc_latest_info_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `market_price`: `Numeric`
  - `market_cap`: `Numeric`
  - `day_trading_volume`: `Numeric`
  - `day_trading_volume_variance`: `Numeric`
  - `hour_price_variance`: `Numeric`
  - `day_price_variance`: `Numeric`
  - `week_price_variance`: `Numeric`
  - `total_supply`: `String`
  - `circulation_supply`: `String`
  - `fully_diluted_market_cap`: `Numeric`
  - `after_day_price_prediction`: `Numeric`
  - `after_day_volume_prediction`: `Numeric`
  - `dominance`: `Numeric`
  - `cmc_rank`: `Integer`
  - `now_move`: `String`
  - `hour_before_move`: `String`
  - `hour_before_move_result`: `String`
  - `two_hour_before_move`: `String`
  - `two_hour_before_move_result`: `String`
  - `day_low_price`: `Numeric`
  - `day_high_price`: `Numeric`
  - `week_low_price`: `Numeric`
  - `week_high_price`: `Numeric`
  - `month_low_price`: `Numeric`
  - `month_high_price`: `Numeric`
  - `total_low_price`: `Numeric`
  - `total_high_price`: `Numeric`
  - `before_moves`: `String`
  - `before_move_results`: `String`
  - `cmc_idx`: `Integer`

---

## `CcLinkItem`
- **Table Name**: `cryptocurrency_link_item`
- **Columns**:
  - `cc_link_item_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `link_kinds_idx`: `Integer`, ForeignKey: `link_kinds.link_kinds_idx`
  - `cc_link_direct_input`: `String`
  - `cc_link_url`: `String`
  - `cc_link_item_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cc_link_item_update_date`: `DateTime`
  - `cc_link_item_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `cc_link_item`
  - `link_kinds`: Many-to-One relationship with `LinkKinds`, backref: `cc_link_item`

---

## `AiAnomalyDetection`
- **Table Name**: `ai_anomaly_detection`
- **Columns**:
  - `ai_anomaly_detection_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `anomaly_score`: `Numeric`
  - `anomaly_cycle`: `String`
  - `ai_anomaly_detection_actual_date`: `DateTime`
  - `ai_anomaly_detection_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `ai_anomaly_detection`

---

## `AiCandlestickPrediction`
- **Table Name**: `ai_candlestick_prediction`
- **Columns**:
  - `ai_candlestick_prediction_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `move_prediction`: `String`
  - `ai_candlestick_prediction_actual_date`: `DateTime`
  - `ai_candlestick_prediction_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `move_result`: `String`
  - `rate_of_change`: `Numeric`
  - `ai_candlestick_prediction_update_date`: `DateTime`
  - `round_count`: `Integer`
  - `time_code`: `Integer`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `ai_candlestick_prediction`

---

## `AiPriceData`
- **Table Name**: `ai_price_data`
- **Columns**:
  - `ai_price_data_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `market_price`: `Numeric`
  - `day_trading_volume`: `Numeric`
  - `time_code`: `Integer`
  - `round_count`: `Integer`
  - `ai_price_data_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `cmc_idx`: `Integer`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `ai_price_data`

---

## `AiPricePrediction`
- **Table Name**: `ai_price_prediction`
- **Columns**:
  - `ai_price_prediction_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `price_after_day_prediction`: `Numeric`
  - `ai_price_prediction_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `volume_after_day_prediction`: `Numeric`
  - `time_code`: `Integer`

---

## `AiPriceHourPrediction`
- **Table Name**: `ai_price_hour_prediction`
- **Columns**:
  - `ai_price_hour_prediction_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `price_after_hour_prediction`: `Numeric`
  - `ai_price_hour_prediction_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `volume_after_hour_prediction`: `Numeric`
  - `time_code`: `Integer`

---

## `AiPriceHourPredictionApi`
- **Table Name**: `ai_price_hour_prediction_api`
- **Columns**:
  - `ai_price_hour_prediction_api_idx`: `Integer`, Primary Key
  - `pair_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `price_after_hour_prediction`: `Numeric`
  - `ai_price_hour_prediction_api_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `time_code`: `Integer`

---

## `AiPriceHourPredictionApiTmp`
- **Table Name**: `ai_price_hour_prediction_api_tmp`
- **Columns**:
  - `ai_price_hour_prediction_api_tmp_idx`: `Integer`, Primary Key
  - `pair_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `price_after_hour_prediction`: `Numeric`
  - `ai_price_hour_prediction_api_tmp_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `time_code`: `Integer`

---

## `AiValuation`
- **Table Name**: `ai_valuation`
- **Columns**:
  - `ai_valuation_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `ai_valuation_actual_date`: `DateTime`
  - `ai_valuation_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `activity_score`: `Numeric`
  - `interest_score`: `Numeric`
  - `team_score`: `Numeric`
  - `stability_score`: `Numeric`
  - `development_score`: `Numeric`
  - `round_count`: `Integer`
  - `time_code`: `Integer`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `ai_valuation`

---

## `AiValuationIco`
- **Table Name**: `ai_valuation_ico`
- **Columns**:
  - `ai_valuation_ico_idx`: `Integer`, Primary Key
  - `project_score`: `Numeric`
  - `community_score`: `Numeric`
  - `finance_score`: `Numeric`
  - `team_score`: `Numeric`
  - `ico_idx`: `Integer`, ForeignKey: `ico.ico_idx`
  - `ai_valuation_ico_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `ai_valuation_ico_update_date`: `DateTime`
  - `round_count`: `Integer`
  - `time_code`: `Integer`

- **Relationships**:
  - `ico`: Many-to-One relationship with `Ico`, back_populates: `ai_valuation_ico`

---

## `WhitepaperUnivInfo`
- **Table Name**: `whitepaper_univ_info`
- **Columns**:
  - `whitepaper_univ_info_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `cc_univ_score`: `Numeric`

---

## `AiVolumePrediction`
- **Table Name**: `ai_volume_prediction`
- **Columns**:
  - `ai_volume_prediction_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `volume_after_day_prediction`: `Numeric`
  - `ai_volume_prediction_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `round_count`: `Integer`
  - `time_code`: `Integer`

---

## `HeaderInfo`
- **Table Name**: `header_info`
- **Columns**:
  - `header_info_idx`: `Integer`, Primary Key
  - `total_market_cap`: `Numeric`
  - `total_day_volume`: `Numeric`
  - `btc_dominance`: `Numeric`
  - `eth_dominance`: `Numeric`
  - `fast`: `Integer`
  - `standard`: `Integer`
  - `slow`: `Integer`
  - `header_info_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`


---

## `Exchange`
- **Table Name**: `exchange`
- **Columns**:
  - `exchange_idx`: `Integer`, Primary Key
  - `exchange_name`: `String`
  - `exchange_logo_file_path`: `String`
  - `exchange_type_common_code`: `String`
  - `exchange_launched_date`: `Date`
  - `market_share_percent`: `String`
  - `maker_fee`: `Numeric`
  - `taker_fee`: `Numeric`
  - `open_interests`: `Numeric`
  - `exchange_site_url`: `String`
  - `exchange_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `exchange_update_date`: `DateTime`
  - `exchange_use_yn`: `String`, Default: `'Y'`
  - `exchange_cmc_idx`: `Numeric`
  - `fiats`: `String`
  - `exchange_slug`: `String`

- **Relationships**:
  - `exchange_currency_item`: One-to-Many relationship with `ExchangeCurrencyItem`, back_populates: `exchange`
  - `exchange_link_item`: One-to-Many relationship with `ExchangeLinkItem`, back_populates: `exchange`
  - `exchange_volume`: One-to-Many relationship with `ExchangeVolume`, back_populates: `exchange`
  - `pair`: One-to-Many relationship with `Pair`, back_populates: `exchange`

---

## `Pair`
- **Table Name**: `pair`
- **Columns**:
  - `pair_idx`: `Integer`, Primary Key
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `exchange_idx`: `Integer`, ForeignKey: `exchange.exchange_idx`
  - `pair_name`: `String`
  - `pair_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `pair_update_date`: `DateTime`
  - `pair_type_common_code`: `String`
  - `pair_use_yn`: `String`, Default: `'Y'`
  - `pair_url`: `String`
  - `cmc_idx`: `Integer`
  - `exchange_cmc_idx`: `Integer`
  - `sub_cmc_idx`: `Integer`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `pair`
  - `exchange`: Many-to-One relationship with `Exchange`, back_populates: `pair`
  - `pair_trade`: One-to-Many relationship with `PairTrade`, back_populates: `pair`

---

## `ExchangeCurrencyItem`
- **Table Name**: `exchange_currency_item`
- **Columns**:
  - `exchange_currency_item_idx`: `Integer`, Primary Key
  - `exchange_idx`: `Integer`, ForeignKey: `exchange.exchange_idx`
  - `currency_idx`: `Integer`, ForeignKey: `currency.currency_idx`
  - `exchange_currency_item_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `exchange_currency_item_update_date`: `DateTime`
  - `exchange_currency_item_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `exchange`: Many-to-One relationship with `Exchange`, back_populates: `exchange_currency_item`
  - `currency`: Many-to-One relationship with `Currency`, back_populates: `exchange_currency_item`

---

## `ExchangeLinkItem`
- **Table Name**: `exchange_link_item`
- **Columns**:
  - `exchange_link_item_idx`: `Integer`, Primary Key
  - `exchange_idx`: `Integer`, ForeignKey: `exchange.exchange_idx`
  - `link_kinds_idx`: `Integer`, ForeignKey: `link_kinds.link_kinds_idx`
  - `exchange_link_url`: `String`
  - `exchange_link_direct_input`: `String`
  - `exchange_link_item_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `exchange_link_item_update_date`: `DateTime`
  - `exchange_link_item_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `exchange`: Many-to-One relationship with `Exchange`, back_populates: `exchange_link_item`
  - `link_kinds`: Many-to-One relationship with `LinkKinds`, backref: `exchange_link_item`

---

## `ExchangeVolume`
- **Table Name**: `exchange_volume`
- **Columns**:
  - `exchange_volume_idx`: `Integer`, Primary Key
  - `exchange_idx`: `Integer`, ForeignKey: `exchange.exchange_idx`
  - `day_trading_volume`: `Numeric`
  - `day_effective_liquidity`: `Numeric`
  - `derivative_volume`: `Numeric`
  - `spot_volume`: `Numeric`
  - `open_interest`: `Numeric`
  - `exchange_score`: `Numeric`
  - `traffic_score`: `Numeric`
  - `exchange_volume_actual_date`: `DateTime`
  - `exchange_volume_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `fake_idx`: `Integer`
  - `exchange_cmc_idx`: `Integer`
  - `day_trading_volume_variance`: `Numeric`
  - `week_trading_volume`: `Numeric`
  - `week_trading_volume_variance`: `Numeric`
  - `round_count`: `Integer`
  - `time_code`: `Integer`

- **Relationships**:
  - `exchange`: Many-to-One relationship with `Exchange`, back_populates: `exchange_volume`

---

## `PairTrade`
- **Table Name**: `pair_trade`
- **Columns**:
  - `pair_trade_idx`: `Integer`, Primary Key
  - `pair_idx`: `Integer`, ForeignKey: `pair.pair_idx`
  - `exchange_price`: `Numeric`
  - `orderbook_minus_2depth`: `Numeric`
  - `orderbook_plus_2depth`: `Numeric`
  - `exchange_volume`: `Numeric`
  - `exchange_volume_percentage`: `Numeric`
  - `pair_trade_date`: `DateTime`
  - `pair_trade_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `round_count`: `Integer`

- **Relationships**:
  - `pair`: Many-to-One relationship with `Pair`, back_populates: `pair_trade`

---

## `PairTradeApi`
- **Table Name**: `pair_trade_api`
- **Columns**:
  - `pair_trade_api_idx`: `Integer`, Primary Key
  - `pair_idx`: `Integer`, ForeignKey: `pair.pair_idx`
  - `exchange_price`: `Numeric`
  - `orderbook_minus_2depth`: `Numeric`
  - `orderbook_plus_2depth`: `Numeric`
  - `exchange_volume`: `Numeric`
  - `exchange_volume_percentage`: `Numeric`
  - `pair_trade_date`: `DateTime`
  - `pair_trade_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `round_count`: `Integer`

---

## `LinkKinds`
- **Table Name**: `link_kinds`
- **Columns**:
  - `link_kinds_idx`: `Integer`, Primary Key
  - `link_name`: `String`

- **Relationships**:
  - `cc_link_item`: One-to-Many relationship with `CcLinkItem`
  - `exchange_link_item`: One-to-Many relationship with `ExchangeLinkItem`

---

## `Member`
- **Table Name**: `member`
- **Columns**:
  - `member_idx`: `Integer`, Primary Key
  - `member_email`: `String`, Unique
  - `password`: `String`
  - `temporary_password`: `String`
  - `temporary_password_regist_date`: `DateTime`
  - `member_image_file_path`: `String`
  - `member_name`: `String`
  - `member_grade_idx`: `Integer`, ForeignKey: `member_grade.member_grade_idx`, Default: `0`
  - `password_change_date`: `DateTime`
  - `member_block_yn`: `String`, Default: `'N'`
  - `member_block_date`: `String`
  - `member_block_term`: `String`
  - `member_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `member_update_date`: `DateTime`
  - `member_secession_date`: `DateTime`
  - `member_use_yn`: `String`, Default: `'Y'`
  - `member_special_code`: `String`

- **Relationships**:
  - `member_grade`: Many-to-One relationship with `MemberGrade`, back_populates: `member`
  - `cc_ai_suggestion`: One-to-Many relationship with `CcAiSuggestion`, back_populates: `member`
  - `cc_alarm`: One-to-Many relationship with `CcAlarm`, back_populates: `member`
  - `ico_alarm`: One-to-Many relationship with `IcoAlarm`, back_populates: `member`
  - `member_agreement_item`: One-to-Many relationship with `MemberAgreementItem`, back_populates: `member`
  - `member_log`: One-to-Many relationship with `MemberLog`, back_populates: `member`
  - `member_sns_item`: One-to-Many relationship with `MemberSnsItem`, back_populates: `member`
  - `portfolio`: One-to-Many relationship with `Portfolio`, back_populates: `member`
  - `question`: One-to-Many relationship with `Question`, back_populates: `member`
  - `subscription`: One-to-Many relationship with `Subscription`, back_populates: `member`
  - `error_report`: One-to-Many relationship with `ErrorReport`, back_populates: `member`
  - `membership_log`: One-to-Many relationship with `MembershipLog`, back_populates: `member`

---

---

## `MemberAgreementItem`
- **Table Name**: `member_agreement_item`
- **Columns**:
  - `member_agreement_item_idx`: `Integer`, Primary Key
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `agreement_idx`: `Integer`, ForeignKey: `agreement.agreement_idx`
  - `agree_yn`: `String`
  - `member_agreement_item_update_date`: `DateTime`, Default: `datetime.datetime.utcnow`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, back_populates: `member_agreement_item`
  - `agreement`: Many-to-One relationship with `Agreement`, back_populates: `member_agreement_item`

---

## `MemberGrade`
- **Table Name**: `member_grade`
- **Columns**:
  - `member_grade_idx`: `Integer`, Primary Key
  - `member_grade_name`: `String`
  - `grade_summary`: `String`
  - `member_grade_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `member_grade_update_date`: `DateTime`
  - `member_grade_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `member`: One-to-Many relationship with `Member`, back_populates: `member_grade`

---

## `MemberLog`
- **Table Name**: `member_log`
- **Columns**:
  - `member_log_idx`: `Integer`, Primary Key
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `login_date`: `DateTime`
  - `login_success_yn`: `String`
  - `member_ip`: `String`
  - `logout_date`: `DateTime`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, back_populates: `member_log`

---

## `MemberSnsItem`
- **Table Name**: `member_sns_item`
- **Columns**:
  - `member_sns_item_idx`: `Integer`, Primary Key
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `sns_type_idx`: `Integer`, ForeignKey: `sns_type.sns_type_idx`
  - `sns_id`: `String`
  - `sns_token`: `String`
  - `sns_profile`: `String`
  - `member_sns_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `member_sns_update_date`: `DateTime`
  - `member_sns_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, back_populates: `member_sns_item`
  - `sns_type`: Many-to-One relationship with `SnsType`, back_populates: `member_sns_item`

---

## `Portfolio`
- **Table Name**: `portfolio`
- **Columns**:
  - `portfolio_idx`: `Integer`, Primary Key
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `portfolio_name`: `String`
  - `portfolio_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `portfolio_update_date`: `DateTime`
  - `portfolio_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, back_populates: `portfolio`

---

## `PortfolioItem`
- **Table Name**: `portfolio_item`
- **Columns**:
  - `portfolio_item_idx`: `Integer`, Primary Key
  - `portfolio_idx`: `Integer`, ForeignKey: `portfolio.portfolio_idx`
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `buy_sell_remittance`: `String`
  - `price_per_cc`: `Numeric`
  - `cc_quantity`: `Numeric`
  - `fees`: `Numeric`
  - `trade_date`: `Date`
  - `memo`: `String`
  - `send_quantity`: `Numeric`
  - `receive_quantity`: `Numeric`
  - `portfolio_item_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `portfolio_item_update_date`: `DateTime`
  - `portfolio_item_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `portfolio_item`

---

## `Question`
- **Table Name**: `question`
- **Columns**:
  - `question_idx`: `Integer`, Primary Key
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `declaration_yn`: `String`, Default: `'Y'`
  - `question_subject`: `String`
  - `question_note`: `String`
  - `question_file_path`: `String`
  - `question_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `question_update_date`: `DateTime`
  - `question_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, back_populates: `question`
  - `answer`: One-to-Many relationship with `Answer`, back_populates: `question`

---

## `Manager`
- **Table Name**: `manager`
- **Columns**:
  - `manager_idx`: `Integer`, Primary Key
  - `manager_id`: `String`
  - `manager_grade`: `Integer`
  - `manager_name`: `String`
  - `manager_password`: `String`
  - `manager_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `manager_update_date`: `DateTime`
  - `manager_block_yn`: `String`, Default: `'N'`

- **Relationships**:
  - `manager_authority`: One-to-Many relationship with `ManagerAuthority`, back_populates: `manager`
  - `agreement`: One-to-Many relationship with `Agreement`, back_populates: `manager`
  - `answer`: One-to-Many relationship with `Answer`, back_populates: `manager`
  - `news`: One-to-Many relationship with `News`, back_populates: `manager`
  - `news_category`: One-to-Many relationship with `NewsCategory`, back_populates: `manager`
  - `error_report`: One-to-Many relationship with `ErrorReport`, back_populates: `manager`
  - `faq`: One-to-Many relationship with `Faq`, back_populates: `manager`
  - `terms_of_service`: One-to-Many relationship with `TermsOfService`, back_populates: `manager`
  - `privacy`: One-to-Many relationship with `Privacy`, back_populates: `manager`

---

## `ManagerAuthority`
- **Table Name**: `manager_authority`
- **Columns**:
  - `manager_authority_idx`: `Integer`, Primary Key
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `authority_idx`: `Integer`, ForeignKey: `authority.authority_idx`
  - `authority_approval_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `manager_authority`
  - `authority`: Many-to-One relationship with `Authority`, back_populates: `manager_authority`

---

## `Agreement`
- **Table Name**: `agreement`
- **Columns**:
  - `agreement_idx`: `Integer`, Primary Key
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `agreement_name`: `String`
  - `agreement_summary`: `String`
  - `agreement_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `agreement_update_date`: `DateTime`
  - `agreement_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `agreement`
  - `member_agreement_item`: One-to-Many relationship with `MemberAgreementItem`, back_populates: `agreement`

---

## `Answer`
- **Table Name**: `answer`
- **Columns**:
  - `answer_idx`: `Integer`, Primary Key
  - `question_idx`: `Integer`, ForeignKey: `question.question_idx`
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `answer_note`: `String`
  - `answer_read_yn`: `String`, Default: `'N'`
  - `answer_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `answer_update_date`: `DateTime`
  - `answer_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `question`: Many-to-One relationship with `Question`, back_populates: `answer`
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `answer`

---


---

## `NewsCategory`
- **Table Name**: `news_category`
- **Columns**:
  - `news_category_idx`: `Integer`, Primary Key
  - `news_category_name`: `String`
  - `news_category_use_yn`: `String`, Default: `'Y'`
  - `news_category_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `news_category_update_date`: `DateTime`
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `news_category`

---

## `News`
- **Table Name**: `news`
- **Columns**:
  - `news_idx`: `Integer`, Primary Key
  - `news_subject`: `String`
  - `news_image_file_path`: `String`
  - `news_note`: `String`
  - `news_source`: `String`
  - `news_contents`: `String`
  - `news_link`: `String`
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `news_actual_date`: `DateTime`
  - `news_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `news_update_date`: `DateTime`
  - `news_use_yn`: `String`, Default: `'Y'`
  - `news_temp_yn`: `String`, Default: `'N'`
  - `round_count`: `Integer`
  - `news_direct_yn`: `String`
  - `news_category`: `String`
  - `news_category_idx`: `Integer`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `news`
  - `news_item`: One-to-Many relationship with `NewsItem`, back_populates: `news`

---

## `NewsItem`
- **Table Name**: `news_item`
- **Columns**:
  - `news_item_idx`: `Integer`, Primary Key
  - `news_idx`: `Integer`, ForeignKey: `news.news_idx`
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `round_count`: `Integer`

- **Relationships**:
  - `news`: Many-to-One relationship with `News`, back_populates: `news_item`
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `news_item`

---

## `Position`
- **Table Name**: `position`
- **Columns**:
  - `position_idx`: `Integer`, Primary Key
  - `position_name`: `String`

- **Relationships**:
  - `contributor`: One-to-Many relationship with `Contributor`, back_populates: `position`

---

## `SnsType`
- **Table Name**: `sns_type`
- **Columns**:
  - `sns_type_idx`: `Integer`, Primary Key
  - `sns_name`: `String`
  - `sns_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `sns_update_date`: `DateTime`
  - `sns_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `member_sns_item`: One-to-Many relationship with `MemberSnsItem`, back_populates: `sns_type`

---

## `Authority`
- **Table Name**: `authority`
- **Columns**:
  - `authority_idx`: `Integer`, Primary Key
  - `authority_name`: `String`
  - `authority_summary`: `String`
  - `column3`: `String`
  - `column4`: `String`

- **Relationships**:
  - `manager_authority`: One-to-Many relationship with `ManagerAuthority`, back_populates: `authority`

---

## `Contributor`
- **Table Name**: `contributor`
- **Columns**:
  - `contributor_idx`: `Integer`, Primary Key
  - `position_idx`: `Integer`, ForeignKey: `position.position_idx`
  - `position_name`: `String`
  - `contributor_type_common_code`: `String`
  - `contributor_name`: `String`
  - `contributor_linked_in_url`: `String`
  - `sns_url`: `String`
  - `introduce`: `String`
  - `contributor_email`: `String`
  - `contributor_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `contributor_update_date`: `DateTime`
  - `contributor_use_yn`: `String`, Default: `'Y'`
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `contributor_file_path`: `String`

- **Relationships**:
  - `position`: Many-to-One relationship with `Position`, back_populates: `contributor`
  - `cc`: Many-to-One relationship with `Cryptocurrency`, back_populates: `contributor`

---

## `ErrorReport`
- **Table Name**: `error_report`
- **Columns**:
  - `error_report_idx`: `Integer`, Primary Key
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `error_report_reference_type`: `String`
  - `error_report_reference_idx`: `Integer`
  - `error_report_subject`: `String`
  - `error_report_note`: `String`
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `processing_date`: `DateTime`
  - `error_report_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `error_report_update_date`: `DateTime`
  - `error_report_use_yn`: `String`, Default: `'N'`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `error_report`
  - `member`: Many-to-One relationship with `Member`, back_populates: `error_report`

---

## `Faq`
- **Table Name**: `faq`
- **Columns**:
  - `faq_idx`: `Integer`, Primary Key
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `faq_subject`: `String`
  - `faq_note`: `String`
  - `faq_language`: `String`
  - `faq_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `faq_update_date`: `DateTime`
  - `faq_use_yn`: `String`, Default: `'Y'`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `faq`

---

## `TermsOfService`
- **Table Name**: `terms_of_service`
- **Columns**:
  - `tos_idx`: `Integer`, Primary Key
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `tos_language`: `String`
  - `tos_content`: `String`
  - `tos_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `tos_language_name`: `String`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `terms_of_service`

---

## `Privacy`
- **Table Name**: `privacy`
- **Columns**:
  - `privacy_idx`: `Integer`, Primary Key
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `privacy_language`: `String`
  - `privacy_content`: `String`
  - `privacy_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `privacy_language_name`: `String`

- **Relationships**:
  - `manager`: Many-to-One relationship with `Manager`, back_populates: `privacy`

---

## `MembershipLog`
- **Table Name**: `membership_log`
- **Columns**:
  - `membership_idx`: `Integer`, Primary Key, AutoIncrement
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `payment_platform`: `String`
  - `payment_plan_id`: `String`
  - `subscribe_id`: `String`
  - `membership_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `membership_price`: `String`
  - `agency_idx`: `Integer`
  - `paid_yn`: `String`, Default: `'N'`

- **Relationships**:
  - `member`: Many-to-One relationship with `Member`, back_populates: `membership_log`

---

---

## `Agency`
- **Table Name**: `agency`
- **Columns**:
  - `agency_idx`: `Integer`, Primary Key, AutoIncrement
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `bank_name`: `String`
  - `account_number`: `String`
  - `account_holder`: `String`
  - `referral_code`: `String`
  - `commission_rate`: `String`
  - `contract_url`: `String`
  - `agency_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `agency_update_date`: `DateTime`
  - `agency_end_date`: `DateTime`
  - `agency_use_yn`: `String`, Default: `'Y'`

---

## `AgencyMemberLog`
- **Table Name**: `agency_member_log`
- **Columns**:
  - `agency_member_idx`: `Integer`, Primary Key, AutoIncrement
  - `agency_idx`: `Integer`, ForeignKey: `agency.agency_idx`
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `agency_member_start_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `agency_member_end_date`: `DateTime`

---

## `MembershipPrice`
- **Table Name**: `membership_price`
- **Columns**:
  - `membership_price_idx`: `Integer`, Primary Key, AutoIncrement
  - `membership_price`: `Numeric`
  - `membership_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `currency_idx`: `Integer`

---

## `Banner`
- **Table Name**: `banner`
- **Columns**:
  - `banner_idx`: `Integer`, Primary Key, AutoIncrement
  - `banner_subject`: `String`
  - `banner_image_file_path`: `String`
  - `banner_link`: `String`
  - `banner_language`: `String`
  - `banner_view_yn`: `String`, Default: `'Y'`
  - `banner_use_yn`: `String`, Default: `'Y'`
  - `banner_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `banner_update_date`: `DateTime`

---

## `AgencyBilling`
- **Table Name**: `agency_billing`
- **Columns**:
  - `agency_billing_idx`: `Integer`, Primary Key, AutoIncrement
  - `agency_idx`: `Integer`, ForeignKey: `agency.agency_idx`
  - `billing_price`: `Numeric`
  - `billing_status`: `String`, Default: `'N'`
  - `billing_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `billing_update_date`: `DateTime`
  - `billing_date`: `DateTime`
  - `billing_month`: `String`
  - `member_count`: `Integer`

---

## `CmsScoreList`
- **Table Name**: `cms_score_list`
- **Columns**:
  - `idx`: `Integer`, Primary Key, AutoIncrement
  - `cc_idx`: `Integer`, ForeignKey: `cryptocurrency.cc_idx`
  - `cc_name`: `String`
  - `cc_code`: `String`
  - `logo_file_path`: `String`
  - `sum_score`: `Numeric`

---

## `MemberFcmToken`
- **Table Name**: `member_fcm_token`
- **Columns**:
  - `member_fcm_token_idx`: `Integer`, Primary Key, AutoIncrement
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `fcm_token`: `String`
  - `device`: `String`
  - `member_fcm_token_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `member_fcm_token_update_date`: `DateTime`

---

## `AppAlarm`
- **Table Name**: `app_alarm`
- **Columns**:
  - `app_alarm_idx`: `Integer`, Primary Key, AutoIncrement
  - `app_alarm_type`: `String`
  - `app_alarm_subject`: `String`
  - `app_alarm_content`: `String`
  - `app_alarm_count`: `Integer`
  - `manager_idx`: `Integer`, ForeignKey: `manager.manager_idx`
  - `app_alarm_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`

---

## `AppAlarmItem`
- **Table Name**: `app_alarm_item`
- **Columns**:
  - `app_alarm_item_idx`: `Integer`, Primary Key, AutoIncrement
  - `app_alarm_idx`: `Integer`, ForeignKey: `app_alarm.app_alarm_idx`
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`

---

## `MemberOpenapi`
- **Table Name**: `member_openapi`
- **Columns**:
  - `member_openapi_idx`: `Integer`, Primary Key, AutoIncrement
  - `member_idx`: `Integer`, ForeignKey: `member.member_idx`
  - `member_openapi_key`: `String`
  - `member_openapi_regist_date`: `DateTime`, Default: `datetime.datetime.utcnow`
  - `member_openapi_use_yn`: `String`, Default: `'Y'`

---








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





