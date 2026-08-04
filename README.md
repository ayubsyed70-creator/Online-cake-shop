# Online Cake Shop — User Stories (INVEST + Gherkin)

**Format:** As a `<who>`, I want `<what>`, so that `<why>`.
**Related artifacts:** `cake-shop-modules-requirements.md`, `cake-shop-use-case.puml/.png`, `cake-shop-process.bpmn/.png`

---

## 1. Initial backlog (by epic)

### Epic: Cake Catalog & Browsing
- **US1.** As a customer, I want to search cakes by keyword, so that I can quickly find a specific cake.
- **US2.** As a customer, I want to filter cakes by dietary tag (eggless/vegan), so that I can find cakes that meet my dietary needs.

### Epic: Cake Customization
- **US3.** As a customer, I want to customize my cake's flavor, size, and message, so that it matches my occasion. *(too big — see split below)*

### Epic: Cart & Checkout
- **US4.** As a customer, I want to pay online for my order, so that I can complete my purchase without visiting the store.
- **US5.** As a customer, I want to be notified if my payment fails, so that I can retry or choose another payment method.

### Epic: Order Management
- **US6.** As a bakery staff member, I want to view order details and customization notes, so that I prepare the cake correctly.
- **US7.** As a bakery staff member, I want a cake that fails quality check sent back to preparation, so that only cakes meeting our standard are shipped.

### Epic: Delivery Management
- **US8.** As a delivery partner, I want to see the pickup and delivery address, so that I can deliver the cake to the right place.
- **US9.** As a customer, I want to track my order status, so that I know when to expect delivery.

### Epic: Ratings & Reviews
- **US10.** As a customer, I want to rate and review my order after delivery, so that I can share feedback with other customers.

### Epic: Admin
- **US11.** As an admin, I want to manage the cake catalog, so that pricing and availability stay up to date. *(too big — see split below)*
- **US12.** As an admin, I want to view sales reports, so that I can track business performance.

---

## 2. Applying INVEST

| Story | Independent | Negotiable | Valuable | Estimable | Small | Testable | Verdict |
|---|---|---|---|---|---|---|---|
| US1 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US2 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US3 | No — bundles 3 independent choices | Yes | Yes | Hard to estimate as one unit | **No** | Hard to test as one unit | **Split** |
| US4 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US5 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US6 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US7 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US8 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US9 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US10 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |
| US11 | No — bundles add/edit/retire | Yes | Yes | Hard to estimate as one unit | **No** | Hard to test as one unit | **Split** |
| US12 | Yes | Yes | Yes | Yes | Yes | Yes | Keep as-is |

### Split: US3 → Cake Customization
- **US3a.** As a customer, I want to choose my cake's flavor, so that it matches my taste preference.
- **US3b.** As a customer, I want to choose my cake's size/weight, so that it fits the number of guests I'm serving.
- **US3c.** As a customer, I want to add a custom message on my cake, so that it's personalized for the occasion.

### Split: US11 → Catalog Management
- **US11a.** As an admin, I want to add a new cake to the catalog, so that customers can order newly available items.
- **US11b.** As an admin, I want to edit an existing cake's price or details, so that the catalog stays accurate.
- **US11c.** As an admin, I want to retire a cake from the catalog, so that customers can't order items we no longer offer.

**Final backlog size:** 12 original stories → 16 after splitting (US3 and US11 replaced by 3 stories each).

---

## 3. Gherkin acceptance criteria (5+ stories)

### US1 — Search cakes by keyword
```gherkin
Feature: Cake search

  Scenario: Customer finds a cake using a keyword
    Given the customer is on the cake catalog page
    When they enter "chocolate" in the search box
    Then the system displays all cakes whose name or description contains "chocolate"

  Scenario: Search with no matches
    Given the customer is on the cake catalog page
    When they enter a keyword that matches no cakes
    Then the system displays a "no cakes found" message instead of an empty page
```

### US4 — Pay online for an order
```gherkin
Feature: Online payment

  Scenario: Successful payment confirms the order
    Given the customer has items in their cart and has entered a valid payment method
    When they submit payment
    Then the system confirms the order and shows an order confirmation number

  Scenario: Cart total matches the amount charged
    Given the customer's cart total is a specific amount
    When they proceed to payment
    Then the amount charged equals the displayed cart total including delivery charges
```

### US5 — Payment failure notification
```gherkin
Feature: Payment failure handling

  Scenario: Customer is notified when payment fails
    Given the customer has submitted payment for their order
    When the payment gateway declines the transaction
    Then the system shows a payment-failed message with the reason
    And no order is created

  Scenario: Customer can retry after a failed payment
    Given the customer has just seen a payment-failed message
    When they choose to retry
    Then the system returns them to checkout with their cart intact
```

### US7 — Failed quality check sent back to preparation
```gherkin
Feature: Quality check

  Scenario: Cake fails quality check
    Given a cake has been prepared and is under quality check
    When the bakery staff marks the quality check as "Fail"
    Then the order status returns to "In Preparation"
    And the cake is not sent to packaging

  Scenario: Cake passes quality check
    Given a cake has been prepared and is under quality check
    When the bakery staff marks the quality check as "Pass"
    Then the order status changes to "Ready for Packaging"
```

### US9 — Track order status
```gherkin
Feature: Order tracking

  Scenario: Customer views current order status
    Given the customer has a confirmed order
    When they open "Track Order"
    Then they see the current status (e.g. In Preparation, Out for Delivery, Delivered)

  Scenario: Status updates after delivery
    Given the delivery partner has marked the order as delivered
    When the customer refreshes "Track Order"
    Then the status shows "Delivered" with the delivery timestamp
```

### US10 — Rate and review after delivery
```gherkin
Feature: Post-delivery review

  Scenario: Customer submits a review after delivery
    Given the customer's order status is "Delivered"
    When they submit a star rating and written review
    Then the review is saved and shown on the cake's catalog page

  Scenario: Customer cannot review before delivery
    Given the customer's order status is not yet "Delivered"
    When they try to open the review form
    Then the system does not allow a review to be submitted
```

---

## 4. AI-assist note

An initial draft of these stories was generated from the module requirements
using a local LLM (Ollama), then manually rewritten to:
- Split two stories that bundled multiple independent choices (US3, US11)
- Rephrase acceptance criteria as concrete Given/When/Then scenarios rather than vague pass/fail conditions
- Add the "no order created" and "cart intact on retry" assertions to the payment scenarios, which the first draft omitted
