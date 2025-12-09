# Software Requirements Specification (SRS)
## Food Court Pre-Order & Queue Optimization System

---

# 1. Introduction

## 1.1 Purpose
This SRS describes the requirements for a mobile/web application that enables students, faculty, and staff to pre-order food from the campus food court.  
The system aims to reduce waiting time, eliminate queues, optimize vendor workload, and prevent fake/unclaimed orders.

## 1.2 Scope
The system includes:
- User app for pre-ordering
- Vendor dashboard
- Admin portal  
Features include:
- Menu browsing
- Time-slot-based ordering
- Online/offline payments
- QR-based pickup
- Real-time status tracking
- Anti-fake order measures

## 1.3 Definitions
- **User** – Student/Faculty/Staff  
- **Vendor** – Stall operator  
- **Admin** – System administrator  
- **Pre-order Window** – Time period when orders are accepted  

---

# 2. Overall Description

## 2.1 Product Perspective
Components:
- User Mobile/Web App  
- Vendor Web Dashboard  
- Admin Web Portal  
- Backend API  
- Database  

## 2.2 Product Features
- Pre-order food via time slots  
- Item availability & menu browsing  
- Real-time order tracking  
- Push notifications  
- QR code pickup  
- Payment integration  
- Anti-fake-order mechanisms  

## 2.3 User Characteristics
Users require only basic smartphone or web usage knowledge.

## 2.4 Constraints
- Internet connection required  
- Vendor must update menu availability  
- High traffic during peak hours  
- Authentication via college email  

## 2.5 Assumptions
- All users belong to the institution  
- Vendors maintain accurate menu & availability  
- Payment gateways are functional  

---

# 3. Functional Requirements

## 3.1 User Module
| ID | Requirement |
|----|-------------|
| FR-U1 | Users shall register using college email/SSO. |
| FR-U2 | Users shall view menus. |
| FR-U3 | Users shall pre-order food using time slots. |
| FR-U4 | Users shall add items to cart and place orders. |
| FR-U5 | Users shall make online or cash-on-pickup payment. |
| FR-U6 | Users shall receive estimated preparation & pickup time. |
| FR-U7 | Users shall track order status. |
| FR-U8 | Users shall receive notifications. |
| FR-U9 | Users shall view order history. |
| FR-U10 | Users must verify identity using email OTP/ID. |
| FR-U11 | System shall allow only one active order per user. |
| FR-U12 | System shall enforce a daily order limit. |
| FR-U13 | System shall generate a unique QR token per order. |
| FR-U14 | Users shall use QR code for pickup. |
| FR-U15 | Mandatory/partial prepayment may be required. |

## 3.2 Vendor Module
| ID | Requirement |
|----|-------------|
| FR-V1 | Vendors shall log in using credentials. |
| FR-V2 | Vendors shall manage menu items and availability. |
| FR-V3 | Vendors shall view/manage incoming orders. |
| FR-V4 | Vendors shall update order status. |
| FR-V5 | Vendors shall set preparation time estimates. |
| FR-V6 | Vendors shall scan the QR code before handing food. |

## 3.3 Admin Module
| ID | Requirement |
|----|-------------|
| FR-A1 | Admin shall manage vendor accounts. |
| FR-A2 | Admin shall view analytics. |
| FR-A3 | Admin shall monitor peak load hours. |
| FR-A4 | Admin shall configure pre-order windows. |
| FR-A5 | Admin shall monitor unclaimed orders & penalized users. |

---

# 4. Non-Functional Requirements

## 4.1 Performance
- API response time < 2 sec  
- Handles peak lunch-time traffic  
- 99% uptime  

## 4.2 Security
- HTTPS/TLS encryption  
- JWT/OAuth authentication  
- Role-based access  
- Anti-fake-order verification  

## 4.3 Usability
- Clean, intuitive UI  
- Easy QR scanning  
- Accessible for all users  

## 4.4 Scalability
- Support multiple stalls  
- Add more food courts seamlessly  

## 4.5 Reliability
- Graceful server recovery  
- Avoid duplicate orders  
- Automatic payment reconciliation  

---

# 5. System Models

## 5.1 Use Case Overview
- Place Order  
- Update Menu  
- Process Payment  
- View/Claim Orders (Vendor)  
- Scan QR for Pickup  
- Admin Monitoring  

## 5.2 Data Flow
User App → Backend → Vendor Dashboard → Backend → User Notifications

---

# 6. Edge Cases

## 6.1 User-Side Edge Cases
- Internet lost during payment  
- Duplicate taps → multiple orders  
- OTP not received  
- Two users order last item simultaneously  
- Time slot becomes full during checkout  
- Payment success but server doesn’t receive callback  
- Low battery → cannot show QR  
- User shares QR code with someone else

## 6.2 Vendor-Side Edge Cases
- Vendor marks item available but stock ends  
- Vendor marks order completed accidentally  
- Vendor dashboard loses network  
- Duplicate QR scans due to lag  

## 6.3 System-Level Edge Cases
- Peak load slows system  
- Race conditions in slot booking  
- Cached menu showing outdated availability  
- Server crash after payment but before order creation  
- CDN outage → menu not loading

## 6.4 Anti-Fake Order Edge Cases
- Incorrect penalty due to vendor mistake  
- Screenshot of QR used by another person  
- QR code reading delay → invalid token shown  
- Multiple no-shows → credibility score issues  

## 6.5 Time Slot Edge Cases
- Slot instantly fills after user selects it  
- User arrives after grace period  
- Vendor shuts stall early → pending orders affected  

## 6.6 Admin-Side Edge Cases
- Admin deletes stall → linked orders break  
- Admin updates time-slot rules mid-day  
- Admin blocks a user with an active order  

## 6.7 Security Edge Cases
- Bot-generated fake orders  
- API tampering to force time slot  
- QR code data manipulation  

---

# 7. Future Enhancements
- AI-based demand prediction  
- NFC-based pickup  
- Subscription meal plans  
- Dynamic time slot allocation  
- User feedback/rating system  

---

# 8. Conclusion
This SRS provides detailed requirements, edge cases, and constraints for a scalable, reliable, and secure preorder system for college food courts. The app focuses heavily on reducing waiting time and preventing fake/unclaimed orders.

