# ClickFunnels 2.0 API Complete Catalog

このドキュメントは、ClickFunnels 2.0 APIの全エンドポイントカタログです。

## 📚 ドキュメント構造

```
docs/clickfunnels/
├── getting-started/       # 5ページ - 認証・OAuth・SSO
├── rest-api/              # 6ページ - 基礎 (Authentication, Pagination, etc.)
├── selling/               # 3ページ - Orders, Fulfillments, Products
├── webhooks/              # 3ページ - Webhooks, Events, Signature Verification
├── funnels/               # 1ページ - Filtering by Page
└── API_CATALOG.md         # このファイル
```

## 🔐 認証

**必須ヘッダー:**
```
Authorization: Bearer YOUR_API_ACCESS_TOKEN
User-Agent: YourAppYourOrg
```

**ベースURL:**
- Accounts: `https://accounts.myclickfunnels.com/api/v2`
- Workspace: `https://{workspace-subdomain}.myclickfunnels.com/api/v2`

## 📊 API Reference - 全エンドポイント

### Team Management

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/teams` | List teams | `/reference/listteams` |
| GET | `/api/v2/teams/{id}` | Fetch team | `/reference/fetchteam` |
| PUT | `/api/v2/teams/{id}` | Update team | `/reference/updateteam` |

### User Management

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/users` | List users | `/reference/listusers` |
| GET | `/api/v2/users/{id}` | Fetch user | `/reference/fetchuser` |
| GET | `/api/v2/users/me` | Fetch current user | `/reference/fetchmyuser` |

### Workspace Management

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces` | List workspaces | `/reference/listworkspaces` |
| GET | `/api/v2/workspaces/{id}` | Fetch workspace | `/reference/getworkspaces` |
| PUT | `/api/v2/workspaces/{id}` | Update workspace | `/reference/updateworkspaces` |

### Appointments & Scheduling

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/appointments/scheduled_events` | List scheduled events | `/reference/listappointmentsscheduledevents` |

### Contact Management

#### Contacts

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/contacts` | List contacts | `/reference/listcontacts` |
| POST | `/api/v2/workspaces/{workspace_id}/contacts` | Create contact | `/reference/createcontact` |
| GET | `/api/v2/contacts/{id}` | Fetch contact | `/reference/fetchcontact` |
| PUT | `/api/v2/contacts/{id}` | Update contact | `/reference/updatecontact` |
| DELETE | `/api/v2/contacts/{id}` | Remove contact | `/reference/removecontact` |

#### Applied Tags

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/contacts/applied_tags` | List applied tags | `/reference/listcontactsappliedtags` |
| POST | `/api/v2/contacts/applied_tags` | Create applied tag | `/reference/createcontactsappliedtag` |
| DELETE | `/api/v2/contacts/applied_tags/{id}` | Remove applied tag | `/reference/removecontactsappliedtag` |

#### Contact Tags

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/contacts/tags` | List contact tags | `/reference/listcontactstags` |
| POST | `/api/v2/workspaces/{workspace_id}/contacts/tags` | Create contact tag | `/reference/createcontactstag` |
| GET | `/api/v2/contacts/tags/{id}` | Fetch contact tag | `/reference/fetchcontactstag` |
| PUT | `/api/v2/contacts/tags/{id}` | Update contact tag | `/reference/updatecontactstag` |

### Course Management

#### Courses

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/courses` | List courses | `/reference/listcourses` |
| POST | `/api/v2/workspaces/{workspace_id}/courses` | Create course | `/reference/createcourse` |
| GET | `/api/v2/courses/{id}` | Fetch course | `/reference/fetchcourse` |
| PUT | `/api/v2/courses/{id}` | Update course | `/reference/updatecourse` |
| DELETE | `/api/v2/courses/{id}` | Remove course | `/reference/removecourse` |

#### Enrollments

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/courses/enrollments` | List enrollments | `/reference/listcoursesenrollments` |
| POST | `/api/v2/courses/enrollments` | Create enrollment | `/reference/createcoursesenrollment` |
| GET | `/api/v2/courses/enrollments/{id}` | Fetch enrollment | `/reference/fetchcoursesenrollment` |
| PUT | `/api/v2/courses/enrollments/{id}` | Update enrollment | `/reference/updatecoursesenrollment` |

#### Sections & Lessons

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/courses/sections` | List sections | `/reference/listcoursessections` |
| POST | `/api/v2/courses/sections` | Create section | `/reference/createcoursessection` |
| GET | `/api/v2/courses/lessons` | List lessons | `/reference/listcourseslessons` |
| POST | `/api/v2/courses/lessons` | Create lesson | `/reference/createcourseslesson` |

### Forms & Submissions

#### Forms

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/forms` | List forms | `/reference/listforms` |
| POST | `/api/v2/workspaces/{workspace_id}/forms` | Create form | `/reference/createform` |
| GET | `/api/v2/forms/{id}` | Fetch form | `/reference/fetchform` |
| PUT | `/api/v2/forms/{id}` | Update form | `/reference/updateform` |

#### Field Sets, Fields, Field Options

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/forms/field_sets` | List field sets | `/reference/listformsfieldsets` |
| POST | `/api/v2/forms/field_sets` | Create field set | `/reference/createformsfieldset` |
| GET | `/api/v2/forms/fields` | List fields | `/reference/listformsfields` |
| POST | `/api/v2/forms/fields` | Create field | `/reference/createformsfield` |
| GET | `/api/v2/forms/field_options` | List field options | `/reference/listformsfieldoptions` |

#### Form Submissions

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/forms/submissions` | List submissions | `/reference/listformssubmissions` |
| POST | `/api/v2/forms/submissions` | Create submission | `/reference/createformssubmission` |
| GET | `/api/v2/forms/submissions/{id}` | Fetch submission | `/reference/fetchformssubmission` |

### Funnels

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/funnels` | List funnels | `/reference/listfunnels` |
| GET | `/api/v2/funnels/{id}` | Fetch funnel | `/reference/fetchfunnel` |
| PUT | `/api/v2/funnels/{id}` | Update funnel | `/reference/updatefunnel` |

### Commerce - Orders

#### Orders

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/orders` | List orders | `/reference/listorders` |
| POST | `/api/v2/workspaces/{workspace_id}/orders` | Create order | `/reference/createorder` |
| GET | `/api/v2/orders/{id}` | Fetch order | `/reference/fetchorder` |
| PUT | `/api/v2/orders/{id}` | Update order | `/reference/updateorder` |

#### Orders - Applied Tags

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/orders/applied_tags` | List order applied tags | `/reference/listordersappliedtags` |
| POST | `/api/v2/orders/applied_tags` | Create order applied tag | `/reference/createordersappliedtag` |

#### Orders - Invoices

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/orders/invoices` | List invoices | `/reference/listordersinvoices` |
| POST | `/api/v2/orders/invoices` | Create invoice | `/reference/createordersinvoice` |
| GET | `/api/v2/orders/invoices/{id}` | Fetch invoice | `/reference/fetchordersinvoice` |
| PUT | `/api/v2/orders/invoices/{id}` | Update invoice | `/reference/updateordersinvoice` |

#### Orders - Transactions

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/orders/transactions` | List transactions | `/reference/listorderstransactions` |
| POST | `/api/v2/orders/transactions` | Create transaction | `/reference/createorderstransaction` |
| GET | `/api/v2/orders/transactions/{id}` | Fetch transaction | `/reference/fetchorderstransaction` |

### Commerce - Products

#### Products

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/products` | List products | `/reference/listproducts` |
| POST | `/api/v2/workspaces/{workspace_id}/products` | Create product | `/reference/createproducts` |
| GET | `/api/v2/products/{id}` | Fetch product | `/reference/fetchproduct` |
| PUT | `/api/v2/products/{id}` | Update product | `/reference/updateproduct` |
| DELETE | `/api/v2/products/{id}` | Remove product | `/reference/removeproduct` |

#### Products - Collections

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/products/collections` | List collections | `/reference/listproductscollections` |
| POST | `/api/v2/workspaces/{workspace_id}/products/collections` | Create collection | `/reference/createproductscollection` |

#### Products - Prices

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/products/prices` | List prices | `/reference/listproductsprices` |
| POST | `/api/v2/products/prices` | Create price | `/reference/createproductsprices` |
| GET | `/api/v2/products/prices/{id}` | Fetch price | `/reference/fetchproductsprice` |
| PUT | `/api/v2/products/prices/{id}` | Update price | `/reference/updateproductsprice` |

#### Products - Variants

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/products/variants` | List variants | `/reference/listproductsvariants` |
| POST | `/api/v2/products/{product_id}/variants` | Create variant | `/reference/createproductsvariants` |
| GET | `/api/v2/products/variants/{id}` | Fetch variant | `/reference/fetchproductsvariant` |
| PUT | `/api/v2/products/variants/{id}` | Update variant | `/reference/updateproductsvariant` |

### Commerce - Fulfillments

#### Fulfillments

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/fulfillments` | List fulfillments | `/reference/listfulfillments` |
| POST | `/api/v2/fulfillments` | Create fulfillment | `/reference/createfulfillments` |
| GET | `/api/v2/fulfillments/{id}` | Fetch fulfillment | `/reference/fetchfulfillment` |
| PUT | `/api/v2/fulfillments/{id}` | Update fulfillment | `/reference/updatefulfillment` |

#### Fulfillments - Locations

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/fulfillments/locations` | List locations | `/reference/listfulfillmentslocations` |
| POST | `/api/v2/workspaces/{workspace_id}/fulfillments/locations` | Create location | `/reference/createfulfillmentslocations` |
| GET | `/api/v2/fulfillments/locations/{id}` | Fetch location | `/reference/fetchfulfillmentslocation` |
| PUT | `/api/v2/fulfillments/locations/{id}` | Update location | `/reference/updatefulfillmentslocation` |

### Sales Management (CRM)

#### Pipelines

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/sales/pipelines` | List pipelines | `/reference/listsalespipelines` |
| POST | `/api/v2/workspaces/{workspace_id}/sales/pipelines` | Create pipeline | `/reference/createsalespipeline` |
| GET | `/api/v2/sales/pipelines/{id}` | Fetch pipeline | `/reference/fetchsalespipeline` |
| PUT | `/api/v2/sales/pipelines/{id}` | Update pipeline | `/reference/updatesalespipeline` |

#### Stages

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/sales/stages` | List stages | `/reference/listsalesstages` |
| POST | `/api/v2/sales/stages` | Create stage | `/reference/createsalesstage` |
| GET | `/api/v2/sales/stages/{id}` | Fetch stage | `/reference/fetchsalesstage` |
| PUT | `/api/v2/sales/stages/{id}` | Update stage | `/reference/updatesalesstage` |

#### Opportunities

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/sales/opportunities` | List opportunities | `/reference/listsalesopportunities` |
| POST | `/api/v2/sales/opportunities` | Create opportunity | `/reference/createsalesopportunity` |
| GET | `/api/v2/sales/opportunities/{id}` | Fetch opportunity | `/reference/fetchsalesopportunity` |
| PUT | `/api/v2/sales/opportunities/{id}` | Update opportunity | `/reference/updatesalesopportunity` |

#### Notes

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/sales/opportunities/notes` | List notes | `/reference/listsalesopportunitiesnotes` |
| POST | `/api/v2/sales/opportunities/notes` | Create note | `/reference/createsalesopportunitiesnote` |

### Shipping

#### Location Groups

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/shipping/location_groups` | List location groups | `/reference/listshippinglocationgroups` |
| POST | `/api/v2/workspaces/{workspace_id}/shipping/location_groups` | Create location group | `/reference/createshippinglocationgroup` |

#### Packages

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/shipping/packages` | List packages | `/reference/listshippingpackages` |
| POST | `/api/v2/workspaces/{workspace_id}/shipping/packages` | Create package | `/reference/createshippingpackage` |

#### Profiles

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/shipping/profiles` | List profiles | `/reference/listshippingprofiles` |
| POST | `/api/v2/workspaces/{workspace_id}/shipping/profiles` | Create profile | `/reference/createshippingprofile` |

#### Rates & Zones

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/shipping/rates` | List rates | `/reference/listshippingrates` |
| POST | `/api/v2/shipping/rates` | Create rate | `/reference/createshippingrate` |
| GET | `/api/v2/workspaces/{workspace_id}/shipping/zones` | List zones | `/reference/listshippingzones` |
| POST | `/api/v2/workspaces/{workspace_id}/shipping/zones` | Create zone | `/reference/createshippingzone` |

### Store & Content

#### Stores

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/stores` | List stores | `/reference/liststores` |
| POST | `/api/v2/workspaces/{workspace_id}/stores` | Create store | `/reference/createstore` |

#### Pages & Images

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/pages` | List pages | `/reference/listpages` |
| POST | `/api/v2/workspaces/{workspace_id}/pages` | Create page | `/reference/createpage` |
| GET | `/api/v2/images` | List images | `/reference/listimages` |
| POST | `/api/v2/images` | Create image | `/reference/createimage` |

### Webhooks

#### Outgoing Endpoints

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/workspaces/{workspace_id}/webhooks/outgoing/endpoints` | List webhook endpoints | `/reference/listwebhooksoutgoingendpoints` |
| POST | `/api/v2/workspaces/{workspace_id}/webhooks/outgoing/endpoints` | Create webhook endpoint | `/reference/createwebhooksoutgoingendpoint` |
| GET | `/api/v2/webhooks/outgoing/endpoints/{id}` | Fetch webhook endpoint | `/reference/fetchwebhooksoutgoingendpoint` |
| PUT | `/api/v2/webhooks/outgoing/endpoints/{id}` | Update webhook endpoint | `/reference/updatewebhooksoutgoingendpoint` |

#### Outgoing Events

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/webhooks/outgoing/events` | List webhook events | `/reference/listwebhooksoutgoingevents` |
| GET | `/api/v2/webhooks/outgoing/events/{id}` | Fetch webhook event | `/reference/fetchwebhooksoutgoingevent` |

#### Outgoing Event Types

| Method | Endpoint | Description | Reference |
|--------|----------|-------------|-----------|
| GET | `/api/v2/webhooks/outgoing/event_types` | List event types | `/reference/listwebhooksoutgoingeventtypes` |
| GET | `/api/v2/webhooks/outgoing/event_types/{id}` | Fetch event type | `/reference/fetchwebhooksoutgoingeventtype` |

---

## 📊 総合統計

- **総エンドポイント数:** 100+ エンドポイント
- **カテゴリ数:** 14カテゴリ
- **スクレイピング済みドキュメント:** 18ページ
- **カバー範囲:**
  - ✅ Getting Started (5ページ)
  - ✅ REST API基礎 (6ページ)
  - ✅ Selling/Orders/Products/Fulfillments (3ページ)
  - ✅ Webhooks (3ページ)
  - ✅ Funnels (1ページ)
  - 📋 API Reference Catalog (このファイル)

---

## 🔗 関連リンク

- **公式ドキュメント:** https://developers.myclickfunnels.com/docs/intro
- **API Reference:** https://developers.myclickfunnels.com/reference
- **Changelog RSS:** https://developers.myclickfunnels.com/changelog.rss
- **OpenAPI Schema (要認証):** https://myclickfunnels.com/api/v2/openapi.yaml

---

**Last Updated:** 2025-11-16
**Miyabi Framework:** Autonomous Scraping System
