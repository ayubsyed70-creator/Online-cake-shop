# Online Cake Shop — Module-Wise Requirements

**Project:** Online Cake Shop
**Related artifacts:** `cake-shop-process.bpmn` / `.png` (order-to-delivery process)
**Actors:** Customer, System (Online Cake Shop platform), Bakery Staff, Delivery Partner, Admin

This document breaks the Online Cake Shop into modules and lists the
functional requirements for each, mirroring the process modeled in the
BPMN diagram.

---

## 1. Cake Catalog & Browsing

**Description:** Lets a customer discover cakes available for order.

**Requirements**
- FR1.1 The system shall display cakes grouped by category (e.g. Birthday, Wedding, Cupcakes, Eggless, Sugar-free).
- FR1.2 The system shall let the customer filter cakes by flavor, size, dietary tag (eggless/vegan), and price range.
- FR1.3 The system shall let the customer search cakes by keyword.
- FR1.4 The system shall show, for each cake, price, available sizes, photos, ingredients, and estimated preparation time.
- FR1.5 The system shall show real-time availability (e.g. "unavailable for same-day delivery").

---

## 2. Cake Customization

**Description:** Lets a customer personalize a selected cake before adding it to the cart.

**Requirements**
- FR2.1 The system shall ask "Customize this cake?" after a cake is selected.
- FR2.2 If yes, the system shall let the customer choose flavor, size/weight, shape, frosting type, and add a message/text on the cake.
- FR2.3 The system shall let the customer upload a reference image for edible-print cakes.
- FR2.4 The system shall recalculate price automatically as customization choices change.
- FR2.5 If no customization is chosen, the system shall proceed with the default configuration of the selected cake.

---

## 3. Cart & Checkout

**Description:** Lets the customer review, adjust, and pay for their order.

**Requirements**
- FR3.1 The system shall let the customer add/remove cakes and adjust quantity in the cart.
- FR3.2 The system shall let the customer choose a delivery date, time slot, and delivery address.
- FR3.3 The system shall display order total including delivery charges and any applicable discount/coupon.
- FR3.4 The system shall support at least one online payment method (card/UPI/wallet) and validate payment before confirming the order.
- FR3.5 If payment fails, the system shall end the checkout attempt without creating a confirmed order and shall notify the customer of the failure reason.

---

## 4. Order Management (System / Bakery Staff)

**Description:** Internal handling of a paid order from confirmation through to handoff for delivery.

**Requirements**
- FR4.1 On successful payment, the system shall generate a confirmed order and notify Bakery Staff.
- FR4.2 Bakery Staff shall be able to view order details, including customization notes and required delivery date/time.
- FR4.3 Bakery Staff shall mark an order as "In Preparation" and later "Ready for Quality Check."
- FR4.4 The system shall support a quality-check outcome of Pass or Fail; a Fail shall route the order back to preparation rather than creating a new order.
- FR4.5 On a Pass, Bakery Staff shall mark the cake as packaged and ready for pickup by a delivery partner.

---

## 5. Delivery Management

**Description:** Handles handoff to and tracking of the delivery partner.

**Requirements**
- FR5.1 The system shall notify an available delivery partner once a cake is packaged and ready for pickup.
- FR5.2 The delivery partner shall be able to confirm pickup and mark the order as "Out for Delivery."
- FR5.3 The delivery partner shall be able to mark the order as "Delivered" once handed to the customer.
- FR5.4 The system shall update order status visible to the customer at each delivery milestone (Out for Delivery, Delivered).
- FR5.5 The system shall record delivery confirmation and close out the order's delivery workflow.

---

## 6. Ratings & Reviews

**Description:** Lets a customer give feedback after receiving their cake.

**Requirements**
- FR6.1 The system shall prompt the customer to rate (1–5 stars) and review their order after delivery is confirmed.
- FR6.2 The system shall let the customer optionally attach a photo with their review.
- FR6.3 The system shall display average rating and reviews on the cake's catalog page.
- FR6.4 The system shall allow only customers with a delivered order for that cake to submit a review for it.

---

## 7. Admin & Reporting

**Description:** Back-office visibility for shop administrators.

**Requirements**
- FR7.1 Admin shall be able to view all orders, filterable by status (Pending Payment, In Preparation, Quality Check, Out for Delivery, Delivered, Payment Failed).
- FR7.2 Admin shall be able to add, edit, or retire catalog items and pricing.
- FR7.3 Admin shall be able to view daily/weekly order volume and revenue reports.
- FR7.4 Admin shall be able to view quality-check failure rate per cake type to flag recurring preparation issues.

---

## Traceability to the process diagram

| Module | BPMN elements it covers |
|---|---|
| Cake Catalog & Browsing | Browse Cakes, Select Cake |
| Cake Customization | Customize Cake? gateway, Customize Cake |
| Cart & Checkout | Add to Cart, Checkout & Pay, Order Received, Payment Valid? gateway, Payment Failed |
| Order Management | Confirm Order, Prepare Cake, Quality OK? gateway, Package Cake |
| Delivery Management | Ready for Pickup, Pick Up Cake, Deliver Cake, Delivery Confirmed, Update Delivery Status |
| Ratings & Reviews | Cake Delivered, Receive Cake, Rate & Review Order |
| Admin & Reporting | Cross-cutting — not modeled as a swimlane in the process diagram (back-office, not part of the order flow) |
