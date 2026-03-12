# ERS API Documentation

## Overview
To use the API, you need:
- **API token** (Admin → General Config → API Info)
- **Developer key** (requested from technical support)

Requests are sent as `POST` calls to the API endpoint.

### Example
```bash
curl -X POST \
  https://mcvr1465.ourers.com/api/read/orders-by-customer/12345/2021-01-01/2021-01-10/ \
  -d key=dev_key \
  -d token=cust_token
```

Where:
- `12345` = customer id
- `2021-01-01` to `2021-01-10` = date range
- `dev_key` = developer key
- `cust_token` = API token

---

## Endpoints

### SIGN
- **Path:** `/api/sign/`
- **HTTP vars:** none
- **Description:** wrapper for `putSignature()`

### SEND EMAIL
- **Path:** `/api/send/email/template_id/customer_list/`
- **HTTP vars:** none
- **Description:** Sends template `template_id` to all customers in `customer_list`.
- **Notes:** `customer_list` must be comma-separated emails **or** customer ids (not both).

### READ ORDER
- **Path:** `/api/read/order/order_id/read_order_mode/` or `/api/read/order/order_id/`
- **HTTP vars:** none
- **Description:** reads an order

### READ WEBSITE PAGE
- **Path:** `/api/read/webpage/` or `/api/read/webpage/page_id/`
- **HTTP vars:** none
- **Description:** returns page name/path/id list, or full page record when `page_id` provided.

### READ ACCOUNTS
- **Path:** `/api/read/accounts/`
- **HTTP vars:** none
- **Description:** thin wrapper for `getAccounts()`

### READ DOCUMENT
- **Path:** `/api/read/document/`
- **HTTP vars:** `POST name: String`

### READ ERSMAIL FILTERS
- **Path:** `/api/read/ersmail_filters/`
- **Description:** returns all ersmail filters for this account.

### READ ERSMAIL CAMPAIGNS
- **Path:** `/read/ersmail_campaigns/`
- **Description:** returns all ersmail campaigns for this account.

### READ ERSMAIL TEMPLATES
- **Path:** `/read/ersmail_templates/`
- **Description:** returns all ersmail templates for this account.

### READ ACCOUNT
- **Path:** `/api/read/account/customer_id/`
- **Description:** returns customer object for customer id.

### READ ITEM STATUS CHOICES
- **Path:** `/api/read/item_status_choices/`
- **Description:** returns choices from general setting "Serial Number Status Choices".

### READ EMAIL TEMPLATES
- **Path:** `/api/read/email_templates/template_type/`
- **Description:** returns CRM email template list for `template_type`.

### READ NEW CUSTOMERS
- **Path:** `/api/read/customers_count/`
- **Description:** returns total customer count.

### READ CUSTOMERS
- **Path:** `/api/read/customers/`
- **HTTP vars:**
  - `POST searchterm: String`
  - `POST include_tags: String[]`
  - `POST exclude_tags: String[]`
  - `POST customer_id: String`
  - `POST limit: Number (optional)`
- **Description:** fetches customer list based on exclusion criteria.

### READ ORDERS BY CUSTOMER
- **Path:** `/api/read/orders-by-customer/customer_id/start_datetime/end_datetime/`
- **Description:** returns orders for customer in date range.

### READ CRM CUSTOMER NOTES
- **Path:** `/api/read/crm_customer_notes/customer_id/`

### READ CRM TAGS
- **Path:** `/api/read/crm_tags/`

### READ CRM OPTIONS
- **Path:** `/api/read/crm_options/customer_id/`

### READ CRM TASKS
- **Path:** `/api/read/crm_tasks/account_id/`

### READ PAYMENT
- **Path:** `/api/read/payment/payment_id/`

### READ CONTRACT
- **Path:** `/api/read/contract/order_id/format/`
- **Description:** returns contract in `html` or plaintext.

### READ ORDERS
- **Path:** `/api/read/order_counts/`
- **Description:** TODO

### READ GUESTS QUEUE
- **Path:** `/api/read/guest_queue/`

### READ CATEGORIES
- **Path:** `/api/read/categories/`

### READ ITEMS
- **Path:** `/publicapi/read/iteminfo/`
- **Description:** returns up to first 10,000 item records.

### READ ADDONS
- **Path:** `/api/read/addons/`

### READ STATES / CITIES / ZIPS / SURFACES / REFERENCES / PROFILES / OPTIONS
- **Paths:**
  - `/api/read/states/`
  - `/api/read/cities/`
  - `/api/read/zips/`
  - `/api/read/surfaces/`
  - `/api/read/references/`
  - `/api/read/profiles/`
  - `/api/read/options/`

### LOGIN
- **Path:** `/api/login/`
- **HTTP vars:** `POST username: String`, `POST password: String`
- **Description:** returns `phpsessid/key/token`.

### LOGOUT
- **Path:** `/api/logout/`

### TEST
- **Path:** `/api/test/`
- **Description:** returns debug test string.

### SET PIN STATUS
- **Path:** `/api/set_pin_status/status/user_id/`

### SET REGISTER NAME
- **Path:** `/api/set_register_name/`
- **HTTP vars:** `POST register_name: String`

### GET CLOCK PUNCH STATUS
- **Path:** `/api/clock_punch_status/user_id/`

### CLOCK IN / OUT
- **Paths:** `/api/clock/in/`, `/api/clock/out/`
- **HTTP vars:** `POST user_id: String`

### CREATE CRM CATEGORY
- **Path:** `/api/create/crm_category/`
- **HTTP vars:** `POST category: String`, `POST color: String`

### CREATE CLOUDPRINT DOCUMENT
- **Path:** `/api/create/cloudprint/`
- **HTTP vars:** `POST printername: String`, `POST data: String`

### CREATE CRM TAG
- **Path:** `/api/create/crm_tag/`
- **HTTP vars:** `POST category: String`, `POST tag: String`

### CREATE CRM CUSTOMER
- **Path:** `/api/create/crm_customer/`
- **HTTP vars:**
  - `POST customer: Object`
  - `POST customer_tags: String[]`
- **Customer fields:**
  `secondary_email`, `parent_email`, `parent_phone`, `parent_name`, `birth_date`, `reference`, `billing_zip`, `billing_state`, `billing_city`, `billing_address`, `fax_phone`, `mobile_phone`, `work_phone`, `phone`, `company_name`, `email`, `lastname`, `firstname`.

### CREATE CRM CUSTOMER NOTE
- **Path:** `/api/create/crm_customer_note/customer_id/`
- **HTTP vars:** `POST author_id: String`, `POST message: String`

### CREATE CRM OPTION
- **Path:** `/api/create/crm_option/`
- **HTTP vars:** `POST data: Object`

### UPDATE CRM CATEGORY
- **Path:** `/api/update/crm_category/`
- **HTTP vars:** `POST category: String`, `POST name: String`, `POST color: String`

### UPDATE ERSMAIL CAMPAIGNS
- **Path:** `/api/update/ersmail_campaigns/`
- **HTTP vars:** `POST campaigns: Object[]`

### UPDATE DOCUMENT
- **Path:** `/api/update/document/`
- **HTTP vars:** `POST name: String`, `POST type: String`, `POST content: String`

### UPDATE CRM TAG
- **Path:** `/api/update/crm_tag/`
- **HTTP vars:** `POST category: String`, `POST tag: String`, `POST new_tag: String`

### UPDATE TASK
- **Paths:**
  - `/api/update/task/customer_id/task_id/`
  - `/api/update/task/customer_id/new/`
  - `/api/update/task/customer_id/delete/task_id/`
- **HTTP vars:**
  - `POST title: String`
  - `POST notes: String`
  - `POST datetime: String`
  - `POST assigned: String`
  - `POST complete: String`

### UPDATE CRM OPTION
- **Path:** `/api/update/crm_option/`
- **HTTP vars:** `POST optionid: Number`, `POST data: Object`

### UPDATE CUSTOMER CRM OPTIONS
- **Path:** `/api/update/customer/crm_options/`
- **HTTP vars:** `POST customer_id: Number`, `POST option_data: Object`

### UPDATE CUSTOMER
- **Path:** `/api/update/customer/`
- **HTTP vars:** `POST customer: Object`, `POST customer_tags: String[]`

### ADD INTERNAL ORDER NOTE
- **Path:** `/api/update/order/add_internal_order_note/`
- **HTTP vars:** `POST order_id: Number`, `POST note: String`, `POST author: String`

### SUBMIT CUSTOM FIELD
- **Path:** `/api/update/order/submit_custom_field/`
- **HTTP vars:** `POST order_id: Number`, `POST custom_field_id: Number`, `POST value: String`

### UPDATE ORDER ITEM QUANTITY
- **Path:** `/api/update/order/set_qty/`
- **HTTP vars:** `POST order_id: Number`, `POST item_id: String`, `POST item_qty: Number`, `POST set_qty: Number`

### TOGGLE CHECKLIST ITEM
- **Path:** `/api/update/order_checklist/toggle_checklist_item/`
- **HTTP vars:** `POST order_id: Number`, `POST item_id: String`

### DELETE CRM CATEGORY
- **Path:** `/api/delete/crm_category/`
- **HTTP vars:** `POST category: String`

### DELETE CRM TAG
- **Path:** `/api/delete/crm_tag/`
- **HTTP vars:** `POST category: String`, `POST tag: String`

### SEND ERSMAIL SEQUENCE
- **Path:** `/api/send_ersmail_sequence/`
- **HTTP vars:** `POST campaign: Object`, `POST list: Object`

### ROUTE INFO
- **Path:** `/api/routeinfo/driver_id/route_date/`

### TIME CHART
- **Path:** `/api/timechart/item_id/start_date/end_date/`

### LOCATION
- **Path:** `/api/location/`

### AVAILABILITY
- **Paths:**
  - `/api/availability/itemid/start_datetime/end_datetime/`
  - `/api/availability/itemid/date/`

### ACTIVATE / RELOAD GIFT
- **Paths:**
  - `/api/activate_gift/order_id/type_id/amount/card_num/card_exp/card_pin/`
  - `/api/reload_gift/order_id/type_id/amount/card_num/card_exp/card_pin/`
- **Valid type_id:** `dejavoo`, `11` (tgate), `22` (ERS gift cards)

### CHECK GIFT BALANCE
- **Path:** `/api/check_gift_balance/type_id/card_num/card_exp/card_pin/`
- **Valid type_id:** `dejavoo`, `11` (tgate), `22` (ERS gift cards)

### MAKE PAYMENT
- **Path:** `/api/make_payment/order_id/type_id/amount/`
- **HTTP vars:** `POST send_receipt: String`

### CAPTURE PAYMENT
- **Path:** `/api/capture_payment/order_id/payment_id/payment_base_amount/payment_tip_amount/`

### REPORT
- **Path:** `/api/report/report_type/`
- **report_type values:** `best_sellers`, `closeout`, `summary`, `insights`, `payments`

### VOID PAYMENT
- **Path:** `/api/void_payment/order_id/payment_id/`

### REFUND PAYMENT
- **Path:** `/api/refund_payment/order_id/payment_id/`

### MANAGE GUEST LIST
- **Path:** `/api/manage_guest_list/order_id/`
- **HTTP vars:**
  - `POST add_guestid: String`
  - `POST remove_guestid: String`
  - `POST checkin_guestid: String`
  - `POST checkout_guestid: String`
  - `POST searchterm: String`
  - `POST add_guest_item_id: String`
  - `POST approve_guestid: String`

### CREATE ORDER
- **Path:** `/api/create_order/`
- **HTTP vars:** `POST order_data: Object`
- **Notes:** `order_data` keys may include:
  - `start_datetime`, `end_datetime`, `order_status`, `order_source`, `created_by`
  - `miscellaneous_fee`, `general_discount`, `coupon`
  - `location`, `customer`, `options`, `items`
  - `order_id`, `order_session`, `read_guest_queue`

### CREATE CUSTOMER
- **Path:** `/api/create_customer/`
- **HTTP vars:** `POST customer_data: Object`

### UPLOAD PHOTO
- **Path:** `/api/upload_photo/order/order_id/`
- **HTTP vars:** `POST photo: String`
- **Notes:** `photo` is base64 encoded image data.

### IMPORT TAGS FROM OPTIONS
- **Path:** `/api/import_tags_from_options/`

### POINTS
- **Path:** `/api/points/operation/customer_id/point_type/amount/order_id/item_id/`
- **HTTP vars:** `POST notes: String`

### RACING
- **Path:** `/api/racing/`

### INVENTORY OUT
- **Path:** `/api/inventory/out/item_id/serial_number_or_sku/order_id/`
- **HTTP vars:** `POST order_id: Number (optional)`

### INVENTORY IN
- **Path:** `/api/inventory/in/item_id/serial_number_or_sku/order_id/`
- **HTTP vars:**
  - `POST sku_qty: String (optional)`
  - `POST inv_cancel: Boolean`
  - `POST inv_status: String (optional)`

### INVENTORY STATUS
- **Paths:**
  - `/api/inventory/inv_status/item_id/serial_number_or_sku/order_id/`
  - `/api/inventory/inv_status/item_id/serial_number_or_sku/`
- **Notes:** `serial_number` can be specific, `all`, or `out`.

### INVENTORY LIST
- **Paths:**
  - `/api/inventory/list/item_id/available/order_id/`
  - `/api/inventory/list/item_id/all/order_id/`

### INVENTORY SERIAL NUMBERS
- **Paths:**
  - `/api/inventory/serial_numbers/all/inv_status/`
  - `/api/inventory/serial_numbers/in/inv_status/`
  - `/api/inventory/serial_numbers/out/inv_status/`

### UPDATE INVENTORY
- **Path:** `/api/inventory/update/item_id/serial_number_or_sku/`
- **HTTP vars:** `POST inv_status: String`

### ORGANIZATION
- **Path:** `/api/organization/`

### APP SETTINGS
- **Path:** `/api/onboarding/`
