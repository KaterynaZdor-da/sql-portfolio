# Dataset Description

This dataset represents an **e-commerce platform with email marketing and user behavior tracking**.

It contains information about:
- user sessions
- email campaigns
- A/B testing
- user interactions on the website
- product purchases
- marketing costs
- revenue forecasts

---

# Database Tables

## ab_test

Identifies which A/B test a user's first session belongs to.

| Column | Description |
|------|-------------|
| ga_session_id | Unique session identifier |
| test | Name of the A/B test |
| test_group | Experiment group (control / treatment) |

---

## account

Contains information about website subscribers.  
A subscriber is a user who provided their email address for communication.

| Column | Description |
|------|-------------|
| id | Unique subscriber identifier |
| send_interval | Email sending frequency |
| is_verified | Indicates whether the email is verified |
| is_unsubscribed | Indicates whether the user unsubscribed |

---

## account_session

Contains information about sessions during which a user subscription was created.

| Column | Description |
|------|-------------|
| account_id | Subscriber identifier |
| ga_session_id | Session identifier |

---

## email_sent

Contains the list of emails sent to users.

The same email may be sent multiple times if the previous attempt failed.

| Column | Description |
|------|-------------|
| id_message | Email identifier |
| sent_date | Date the email was sent |
| letter_type | Email campaign type |
| id_account | Subscriber identifier |

---

## email_open

Contains information about emails opened by users.

A user may open the same email multiple times.

| Column | Description |
|------|-------------|
| id_message | Email identifier |
| open_date | Date the email was opened |
| letter_type | Email campaign type |
| id_account | Subscriber identifier |

---

## email_visit

Contains information about email link clicks.

A user may click links in the same email multiple times.

| Column | Description |
|------|-------------|
| id_message | Email identifier |
| visit_date | Click date |
| letter_type | Email campaign type |
| id_account | Subscriber identifier |

---

## session

Contains information about user sessions.

| Column | Description |
|------|-------------|
| ga_session_id | Unique session identifier |
| date | Session date |

---

## session_params

Contains additional information about user sessions such as device, browser, and location.

| Column | Description |
|------|-------------|
| ga_session_id | Session identifier |
| device | Device type |
| mobile_model_name | Mobile device model |
| operating_system | Operating system |
| language | Browser language |
| browser | Browser |
| continent | User continent |
| country | User country |
| medium | Traffic medium |
| name | Traffic source name |
| channel | Marketing channel |

---

## event_params

Contains events performed by users on the website.

| Column | Description |
|------|-------------|
| ga_session_id | Session identifier |
| event_timestamp | Event timestamp |
| event_name | Event type |
| event_params | Additional event parameters |

---

## order

Contains information about purchased products.

Multiple products may be purchased within a single session.

| Column | Description |
|------|-------------|
| ga_session_id | Session identifier |
| item_id | Purchased product identifier |

---

## product

Contains information about products available on the website.

| Column | Description |
|------|-------------|
| item_id | Product identifier |
| name | Product name |
| category | Product category |
| price | Product price |
| description | Product description |

---

## paid_search_cost

Contains information about paid traffic acquisition costs.

| Column | Description |
|------|-------------|
| date | Date |
| cost | Advertising cost |

---

## revenue_predict

Contains revenue forecast data.

| Column | Description |
|------|-------------|
| date | Date |
| predict | Revenue prediction |

---

# Key Relationships

The dataset contains several important relationships between tables:

- `session.ga_session_id` connects user activity across multiple tables.
- `account.id` links subscribers with email interactions.
- `product.item_id` links orders to the product catalog.
- `ga_session_id` is the main key used to track user behavior within sessions.

These relationships allow analysis of:

- user behavior on the website
- effectiveness of email campaigns
- conversion to purchases
- marketing performance
