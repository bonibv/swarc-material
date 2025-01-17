</div>

# **PictShare**

<div style="page-break-after: always;"></div>

# Introduction and Goals

* Business Goals: Engage a global community of photography enthusiasts through a feature-rich platform.
* Essential Features: Advanced editing tools, customizable filters, and a robust user community with sharing capabilities.
* Functional Requirements: User profile creation, image sharing with tagging, editing tools, and subscription options.
* Quality Goals: Performance, usability, and security of the architecture.
* Stakeholders: Marketing Manager, Project Manager, Lead Developer, UX/UI Designer, User Representative, and Photography Expert.

## Requirements Overview

<div class="formalpara-title">

**Contents**

</div>


The functional requirements for PictShare can be summarized as follows:

* User Profiles: Ability for users to create and manage personal profiles, connect with others, and curate collections of images.
* Image Sharing: Feature to share images with the community, including tagging and social media integration.
* Advanced Editing Tools: A range of editing capabilities like color correction, white balance, and exposure adjustments.
* Customizable Filters: Options for users to create and save custom filters and select from pre-existing ones.
* Community Engagement: Community-driven features such as challenges, competitions, and a social feed.


<div class="formalpara-title">


## Quality Goals

<div class="formalpara-title">

**Contents**

</div>

* Performance: The app should handle high traffic, ensuring image uploads and edits are processed within seconds.

* Usability: User interfaces should be intuitive, allowing new users to navigate and use advanced features with minimal instruction.

* Security: Adhere to privacy regulations, ensuring user data and content are protected.

<div class="formalpara-title">

**Motivation**

</div>

The PictShare app is designed to enhance the photographic experience by providing a dedicated platform for image sharing and editing, catering to the specific needs of photography enthusiasts and professionals.

<div class="formalpara-title">

## Stakeholders

<div class="formalpara-title">

**Contents**

</div>

| Role/Name   | Contact        | Expectations       |
|-------------|----------------|--------------------|
| *\<Marketing Manager>* | *\<Sarah Chen>* | *\<Brand visibility and user base growth>* |
| *\<Project Manager>* | *\<Michael Nguyen>* | *\<Timely delivery and system stability>* |
| *\<Lead Developer>* | *\<Ava Patel>* | *\<Technical excellence and maintainability>* |
| *\<UX/UI Designer>* | *\<Emily Wong>* | *\<Aesthetic appeal and user-friendly design>* |
| *\<User Representative>* | *\<Samir Singh>* | *\<Community engagement and content richness>* |
| *\<Photography Expert>* | *\<Lucas Rodriguez>* | *\<High image quality and creative tools>* |

<div class="formalpara-title">

# Architecture Constraints

<div class="formalpara-title">

**Contents**

</div>

* Security concerns: Security is a paramount concern, especially in microservices and mobile development. Architects must adhere to security constraints such as authentication, authorization, encryption, and protection against common security vulnerabilities when designing API Gateway patterns. These constraints limit design freedom to prioritize security.
* Interoperability constraints: Cross-platform mobile development often involves multiple platforms (iOS, Android, web). Architects need to ensure that the API Gateway provides consistent and compatible interfaces for different client platforms. This can limit the choice of technologies and APIs used in the development process to ensure seamless interoperability.
* Versioning and Compatibility Constraints: As systems evolve, architects need to maintain backward compatibility to avoid breaking existing clients. This constraint may limit the freedom to make drastic changes in the API or microservices without providing appropriate versioning and migration strategies
* Regulatory and Compliance Constraints: Many industries have specific regulations and compliance requirements (e.g., GDPR). Architects must consider these constraints when designing API Gateway patterns for microservices. Compliance with these rules may necessitate data handling, auditing, and reporting features that could impact architectural choices.

<div class="formalpara-title">

# System Scope and Context

<div class="formalpara-title">

**Contents**

</div>

The PictShare system enables users to upload, edit, and share images. It interacts with external editing tools like Pixlr and social media platforms for sharing, delineating the system's scope. The business context involves user engagement and content distribution, while the technical context covers the APIs, protocols, and hardware necessary for image processing and data storage.

<div class="formalpara-title">

**Motivation**

</div>

Understanding the interfaces with Pixlr for image editing and platforms like Instagram for sharing is critical, as they directly affect the user experience and the performance of the PictShare system.

<div class="formalpara-title">

## Business Context

<div class="formalpara-title">

**Contents**

</div>

PictShare interacts with users and various IT systems for its operations. Users provide image content and interact through the app. Payment services process subscriptions and purchases. Location services enhance user experience with geotagging. The marketing email system facilitates promotional communication. Data storage is managed by the hosting partner.

| Communication Partner | Inputs from PictShare               | Outputs to PictShare              |
|-----------------------|-------------------------------------|-----------------------------------|
| Users                 | Image uploads, profile information  | Edited images, notifications      |
| Payment Service       | Subscription and purchase details   | Payment confirmations             |
| Location Service      | Image data for geotagging           | Location data for images          |
| Email Service         | Parameters for marketing emails     | Confirmation of email delivery    |
| Hosting Partner       | Requests for data storage           | Access to stored user data        |

<div class="formalpara-title">

**Motivation**

</div>

To ensure clarity among stakeholders regarding the flow of information and the system's integration with external services, which is essential for operational success and user satisfaction.

<div class="formalpara-title">

## Technical Context

<div class="formalpara-title">

**Contents**

</div>

The technical context of PictShare includes HTTPS for secure communication with user devices, RESTful API interactions with Pixlr for image editing, and OAuth for secure authorization with social media platforms. The system uses SQL over JDBC for database transactions to store user data and image metadata.

| Domain Interface | Technical Channel | Protocol |
| ---------------- | ----------------- | -------- |
| Image Upload | Server-API | HTTPS |
| Image Editing | Pixlr API | RESTful API |
| Social Media Sharing | Instagram API | OAuth |
| Data Storage | Database Server | SQL over JDBC |

<div class="formalpara-title">

**Motivation**

</div>

These technical interfaces are crucial for ensuring the secure and efficient operation of PictShare. They are of particular interest to infrastructure architects and are fundamental to the system's ability to interact with its technical environment.

<div class="formalpara-title">


# Solution Strategy

<div class="formalpara-title">

**Contents**

</div>

* Technology Decisions: Adoption of a microservices architecture to facilitate scalability and maintainability.
* Top-level Decomposition: Use of APIs to interface with services like Pixlr for image editing and social media platforms for sharing.
* Key Quality Goals Achievement: Emphasis on usability and security through a user-friendly interface and secure API gateways.
* Organizational Decisions: Agile development process with continuous integration and deployment practices.

<div class="formalpara-title">

**Motivation**

</div>

These decisions are fundamental to creating an architecture that is resilient, scalable, and meets the user's needs and business objectives. They provide a framework within which all other architectural and design decisions are made.

<div class="formalpara-title">

# Building Block View

<div class="formalpara-title">

**Content**

</div>

The PictShare system is structured into several key modules: User Interface, Application Server, Database, and External APIs (like Pixlr and social media integrations). Each module has distinct responsibilities and interacts with others to provide the app's functionalities.

Descriptions of Building Blocks:

**Application Server**
_The Application Server is the central hub for processing user requests and delivering content. It hosts the PictShare application logic and ensures efficient handling of simultaneous user activities. Optimized for performance with load balancing to manage high traffic._

**Pixlr Api**
_Integrated for advanced image editing features directly in the PictShare app, allowing users to apply filters and edit images. Chosen for its wide range of functions and reliable service_

**Instagram Api**
_Enables direct sharing of images to Instagram, expanding user reach and simplifying the sharing process. It's implemented with secure OAuth authentication to protect user data._

**Database Node**
_Stores all user data and image metadata. It's configured for high availability and is regularly backed up for data integrity and disaster recovery. Utilizes indexing for quick retrieval of records, enhancing the application's responsiveness._

**Users**
_Represents various end-user devices such as smartphones and laptops. Ensures that PictShare is responsive and provides a seamless experience across all device types through adaptive design and cross-platform compatibility._


**Level 1**

![Screenshot 2024-01-12 at 12 06 52](https://github.com/bonibv/swarc-material/assets/132003411/a127c436-a105-4f35-a0e3-b1a745ffa16f)

**Level 2**

![Screenshot 2024-01-12 at 12 08 51](https://github.com/bonibv/swarc-material/assets/132003411/f6637e6d-00a8-4417-b505-34eda206dab0)


<div class="formalpara-title">

**Motivation**

</div>

This modular architecture supports efficient development and maintenance, ensuring that each component can be updated or scaled independently. It aligns with the app's need for flexibility, scalability, and robust performance.

<div class="formalpara-title">

# Runtime View

<div class="formalpara-title">

**Contents**

</div>

Important Use Cases/Features and Execution:

Image Upload and Edit: Involves user uploading an image, the system processing and storing it, followed by user selecting and applying filters.
Image Sharing: User shares the edited image to social media via system's integration with platforms like Instagram.
Interactions at Critical External Interfaces:

The system interfaces with Pixlr API for image editing and with social media platforms for sharing, facilitating seamless user interaction.

<div class="formalpara-title">

**Motivation**

</div>

Understanding these scenarios is vital for comprehending how the system operates in real-time, particularly focusing on user interaction and the system's response.

<div class="formalpara-title">

**Form**

</div>

## \<Runtime Scenario 1>

-   ![7  SWARC Runtime 1](https://github.com/bonibv/swarc-material/assets/132003411/0277253c-cb8b-4c55-b5c2-96a4c4adf6b9)


## \<Runtime Scenario 2>
-   ![7  SWARC Runtime 2](https://github.com/bonibv/swarc-material/assets/132003411/b922063e-b944-43ad-80da-e70d7f3ace47)

<div style="page-break-after: always;"></div>

# Deployment View

<div class="formalpara-title">

**Content**

</div>

<img width="765" alt="Screenshot 2024-01-16 at 19 46 53" src="https://github.com/bonibv/swarc-material/assets/132003411/4eea2402-3f89-42fb-ad5c-39108ba16dc6">


<div class="formalpara-title">

***\<Overview Diagram>***

Motivation  
*\<The deployment architecture is designed to ensure scalability, high availability, and seamless integration with external services, enhancing the user experience and offering robust data management and sharing capabilities.>*

Quality and/or Performance Features  
*\<The Application Server is optimized for handling high traffic with load balancing.
The Database Node ensures data integrity and supports quick retrieval for a responsive user experience.
External APIs provide specialized services (image editing and social media integration) efficiently.>*

Mapping of Building Blocks to Infrastructure  
*\<Application logic is hosted on the Application Server.
Data is managed by the Database Node.
Pixlr API handles image editing requests.
Instagram API manages sharing functionalities.>*

# Cross-cutting Concepts


**Content**

</div>

## *\<Domain Concepts>*

*\<The domain model of PictShare encapsulates user-generated content, profile management, and interaction. It defines how users interact with the system, including uploading, editing, and sharing images, as well as following and engaging with other users.>*

## *\<User Experience (UX) Concepts>*

*\<PictShare emphasizes a user-centered design approach, focusing on intuitive navigation, responsive interfaces, and accessible editing tools. This ensures a frictionless experience from image upload to final share.>*

## *\<Security Concepts>*
*\<Security is a top priority, with measures such as two-factor authentication, secure image storage, and privacy controls for user profiles and content. Data encryption safeguards against unauthorized access.>*

## *\<Architecture Patterns>*
*\<PictShare may adopt a microservices architecture, where services are loosely coupled, independently deployable, and organized around business capabilities, enhancing the system's flexibility and scalability.>*

## *\<Operational Concepts*
*\<Cloud-based deployment ensures PictShare is scalable and reliable, with continuous monitoring, automated scaling, and disaster recovery processes in place to maintain service availability and performance.>*

## *\<Development Concepts>*
*\<Development follows best practices such as Agile methodologies, test-driven development, and continuous integration/continuous deployment pipelines, enhancing code quality and facilitating rapid iterations.>*

<div style="page-break-after: always;"></div>

# Architecture Decisions

<div class="formalpara-title">

**Contents**

</div>

PictShare's architecture decisions include adopting a microservices architecture for scalability, using cloud-based storage for reliability, and implementing robust security measures for user data protection.

| Problem | Considered Alternatives | Decision |
| ---------------- | ----------------- | -------- |
| Microservices are too expensive | Use a monolith architecture | Hire more DevOps specialists|
| API Gateway Performance Bottlenecks | Implement load balancing and caching mechanisms within the API Gateway to reduce performance bottlenecks | Implement load balancing and caching mechanisms within the API Gateway to improve performance and alleviate bottlenecks |
| Cross-Platform UI Performance Issues | Optimize the application code and UI components for each platform independently to achieve native-like performance, but still retain cross-platform code base | Optimize the application code and UI components for each platform independently to ensure that the cross-platform app delivers a smooth and responsive user experience |

<div class="formalpara-title">

**Motivation**

</div>

These decisions are driven by the need to manage a large user base, ensure high availability of the service, and maintain trust through secure operations.

<div class="formalpara-title">

# Quality Requirements

## Quality Tree

<div class="formalpara-title">

![SWARC 5 Quality Tree](https://github.com/bonibv/swarc-material/assets/132003411/7e2b3b4a-30ba-4e9f-b4d9-422aab12c036)

## Quality Scenarios

<div class="formalpara-title">

**Contents**

</div>

* App Stability
Scenario: The app should not crash, ensuring a consistent user experience.

* Content Moderation:
Scenario: Pictshare should implement an effective content moderation system to prevent the sharing of inappropriate or offensive material. This could involve automated filters, user reporting mechanisms, and a dedicated team for reviewing reported content.

* Community Engagement
Scenario: Users should return to the app weekly, with features like challenges designed to be easy and fun, encouraging regular engagement and helping to maintain a steady user community.

<div class="formalpara-title">

# Risks and Technical Debts

<div class="formalpara-title">

**Contents**

</div>

1. User Experience Impact
Cross-platform development offers cost-efficiency but accumulates technical debt for native features. Ongoing maintenance is essential for competitiveness.

2. Performance and Reliability
User Experience Impact
Cross-platform development offers cost-efficiency but accumulates technical debt for native features. Ongoing maintenance is essential for competitiveness.

3. Performance and Reliability
Centralized API Gateway in microservices introduces risks, technical debt, and performance impacts. Optimization is essential to maintain stability.
Security Vulnerabilities
Cross-platform mobile development accumulates security-related technical debt, requiring ongoing security efforts to manage platform-specific vulnerabilities and ensure resilience to emerging threats, safeguarding user data against breaches and compromises.

<div class="formalpara-title">

# Glossary

<div class="formalpara-title">

**Contents**

</div>

| Term                 | Definition                                                                                          |
|----------------------|-----------------------------------------------------------------------------------------------------|
| HTTPS                | Secure protocol used by PictShare for encrypted communication over a computer network.               |
| RESTful API          | Architectural style for an application program interface (API) that uses HTTP requests to access and use data. |
| OAuth                | An open standard for access delegation commonly used to grant websites or applications access to information on other websites without giving them the passwords. |
| SQL over JDBC        | A method for executing SQL statements using Java Database Connectivity for database interoperability in PictShare. |
| Centralized API Gateway | A single entry point for all clients to manage API calls, routing them to the appropriate services within PictShare. |
| Monolith Architecture | A software development model where PictShare is built as a single, indivisible unit.                 |
| DevOps               | A set of practices that combines software development (Dev) and IT operations (Ops) aimed at shortening the development life cycle of PictShare and providing continuous delivery. |
| Load Balancing       | The process of distributing network or application traffic across multiple servers in PictShare to ensure reliability and performance. |
| Performance Bottlenecks | Points in a system where the performance is limited, PictShare identifies and addresses these to maintain efficiency. |
| UI                   | User Interface - The space where interactions between humans and the PictShare application occur.    |

<div class="formalpara-title">
