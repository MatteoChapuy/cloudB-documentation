# [Getting Started](getting-started.md)

## Creating an Account

### Why an Account is Necessary
CloudB is a SaaS web application, and creating an account is essential for utilizing its capabilities and storing data. All user data are securely managed by Google Cloud, offering a high level of security. Your data are private and will not be shared with third parties.

### Account Creation Steps
1. Navigate to the registration page.
2. Fill in your email address.
3. An email verification will be sent to the provided email address.
4. Check your email and input the verification code on CloudB to complete the registration.

### Customizing Your Profile
Users can personalize their profiles by navigating to `My Account` > `My Account`. Here, you can add or edit your name, surname, company, and user experience preferences.

## Understanding the Different Types of User Accounts

### Account Types
CloudB supports three types of user accounts:
- **Administrator**: Responsible for granting access and managing user accounts. Primarily for internal use within Delhom Acoustique.
- **Intern**: These are internal engineers at Delhom Acoustique, given access by administrators.
- **Client**: External users or clients, also granted access by administrators.

### Access Control by Administrators
Administrators have the ability to manage access rights to various workspaces and applications on the CloudB platform. They can also disable accounts when necessary.

## Understanding CloudB's Architecture

### Workspaces
A workspace in CloudB acts like a toolbox, equipped with specific applications or projects to address distinct noise problems. Every workspace has its own dedicated Google Cloud SQL database where both input and output data are stored securely.

### Projects and Applications
Within a workspace, you can have either projects or applications, both designed to carry out particular tasks or analyses. Projects are more generalized frameworks, whereas applications are specialized tools.

### Technical Architecture
CloudB runs on two separate Google Cloud instances for optimal performance:
- **Frontend Instance**: Handles the user interface and user interactions.
- **Backend Instance**: Manages data processing, allowing for concurrent calculations and requests.

By segregating the frontend and backend, CloudB ensures a seamless and efficient user experience, even when performing multiple tasks simultaneously.

### Use of External APIs
To enhance user experience, CloudB integrates with various external APIs. However, it's important to note that these APIs are not provided with any personal user data unless explicitly stated or required for the service to function. These integrations are solely for the purpose of augmenting features and functionalities within CloudB.