# Samhita Microservice Architecture

The **Samhita** project is built on a microservice architecture, comprising a total of 13 backend microservices:

1. **credit_gurantee_service**
2. **samhita_notification_backend**
3. **ephermal_link_samhita**
4. **samhita_ondc_backend**
5. **pre_credit_score_service**
6. **samhita_otp_backend**
7. **revive_backend**
8. **samhita_rbac_backend**
9. **samhita_appreaciate_user_service**
10. **samhitha_appreciate_backend**
11. **samhita-distributor-agent**

### Overview of Key Microservices

- **samhita-distributor-agent**:  
  This microservice manages entity onboarding for various stakeholders:
  - **IP Onboarding**: Includes onboarding of IP companies, contact persons, and agents.
  - **Funder Onboarding**: Similar to IP onboarding but without the concept of agents.
  - **Lender/NBFC Management**: Manages lender companies, contact persons, and agents.
  - **Samhita Staff Onboarding**: Also includes staff onboarding.

- **samhita_appreaciate_user_service**:  
  Handles participant management, including single and bulk onboarding. Bulk onboarding is achieved through background tasks using Celery and Redis.

- **samhitha_appreciate_backend**:  
  Acts as a User Identity Management (UIM) service, handling all types of user logins and session management on the Samhita platform.

- **samhita_rbac_backend**:  
  Manages Role-Based Access Control (RBAC). This service defines roles for users, with each role connected to specific grants. Grants are associated with modules, and each module has its own set of permissions.

- **samhita_otp_backend**:  
  Responsible for sending both mobile and email OTPs. Mobile OTPs are sent via Text Local, while email OTPs are sent using AWS SES.

- **ephermal_link_samhita**:  
  This service is used for setting and resetting user passwords during the onboarding process.

- **samhita_notification_backend**:  
  Sets up a notification service for the platform, supporting SMS, WhatsApp, and email notifications. Various platform events trigger these notifications to be sent to the appropriate users.

- **revive_backend**:  
  Manages project creation, form creation, and data collection. Projects are created with mappings to IPs and funders. Forms can be mapped to projects, and responses can be collected through single or bulk uploads. This service also supports participant enrollment to projects, data collection by IP agents, and the disbursement and repayment for participants involved in specific projects.
