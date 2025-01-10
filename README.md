# AWS Certified Cloud Practitioner

This is a demo repository for the AWS Certified Cloud Practitioner course.

# Types of Cloud Computing

Cloud computing is broadly categorized into three types based on service models and four types based on deployment models. Here's an overview:

---

## **Service Models**

1. **Infrastructure as a Service (IaaS):**
   - Provides virtualized computing resources over the internet.
   - Includes services like virtual machines, storage, and networks.
   - Allows users to manage and control the infrastructure.
   - **Examples:** AWS EC2, Microsoft Azure Virtual Machines, Google Compute Engine.

2. **Platform as a Service (PaaS):**
   - Offers a platform and environment for developers to build, deploy, and manage applications without worrying about infrastructure.
   - Provides tools and frameworks for development.
   - **Examples:** Heroku, Google App Engine, Microsoft Azure App Service.

3. **Software as a Service (SaaS):**
   - Delivers software applications over the internet on a subscription basis.
   - Managed entirely by the provider, including maintenance and updates.
   - **Examples:** Google Workspace (Docs, Sheets, Gmail), Microsoft 365, Salesforce.

4. **Function as a Service (FaaS):**
   - Often categorized under serverless computing.
   - Allows developers to run specific functions or pieces of code without managing servers.
   - **Examples:** AWS Lambda, Azure Functions, Google Cloud Functions.

---

## **Deployment Models**

1. **Public Cloud:**
   - Resources are owned and operated by a third-party cloud service provider and delivered over the internet.
   - Shared infrastructure is used by multiple organizations or customers.
   - **Examples:** AWS, Google Cloud, Microsoft Azure.

2. **Private Cloud:**
   - Resources are used exclusively by a single organization.
   - Provides greater control and customization.
   - Can be hosted on-premises or by a third-party provider.
   - **Examples:** VMware, OpenStack-based private clouds.

3. **Hybrid Cloud:**
   - Combines public and private clouds, allowing data and applications to be shared between them.
   - Offers flexibility and optimizes existing infrastructure.
   - **Example Use Case:** Sensitive workloads on a private cloud and general-purpose workloads on a public cloud.

4. **Community Cloud:**
   - Shared infrastructure for specific organizations with similar goals, policies, or compliance requirements.
   - Typically managed collectively or by a third party.
   - **Example Use Case:** Government agencies with shared compliance needs.

---

These types can be tailored to meet specific business requirements, offering varying levels of control, flexibility, and cost-effectiveness.


# IAM Permissions

**IAM (Identity and Access Management)** permissions define the actions and resources a user, group, or role can access in a cloud environment. These permissions ensure secure and granular control over resources.

---

## **Key Concepts**

1. **Principals:**
   - Entities (users, groups, roles, or services) that perform actions on resources.
   - Examples:
     - **AWS:** IAM users, groups, roles.
     - **Azure:** Users, service principals, managed identities.
     - **GCP:** Google accounts, service accounts.

2. **Policies:**
   - Documents that define permissions by specifying actions, resources, and conditions.
   - Types:
     - **Allow policies**: Explicitly grant access.
     - **Deny policies**: Explicitly restrict access (overrides allow policies).

3. **Actions:**
   - Operations a principal can perform (e.g., `ec2:StartInstances` in AWS, `storage.buckets.create` in GCP).

4. **Resources:**
   - Cloud objects or entities to which permissions apply, such as VMs, storage buckets, or databases.

5. **Conditions:**
   - Optional criteria that must be met for permissions to apply (e.g., time of access, IP ranges).

---

## **Types of IAM Permissions**

### 1. **User Permissions**
   - Permissions assigned directly to individual users.
   - Best for specific, unique access requirements.

### 2. **Group Permissions**
   - Permissions applied to a group of users.
   - Easier to manage access for teams.

### 3. **Role Permissions**
   - Permissions assigned to roles that can be assumed temporarily.
   - Commonly used for cross-account access and service permissions.

### 4. **Service Account Permissions**
   - Permissions granted to applications or services.
   - Enable secure communication and operations between services.

---

## **Best Practices**

1. **Principle of Least Privilege:**
   - Grant only the permissions necessary to perform a task.

2. **Use Groups and Roles:**
   - Avoid assigning permissions directly to individual users; use groups or roles instead.

3. **Regular Auditing:**
   - Periodically review and update permissions to maintain security.

4. **Conditions for Specificity:**
   - Use conditions to narrow down the scope of access (e.g., restrict access to specific IPs or times).

5. **Enable Multi-Factor Authentication (MFA):**
   - Add an extra layer of security for sensitive permissions.

---

## **IAM Across Cloud Providers**

### **AWS IAM:**
   - Permissions are defined in JSON policy documents.
   - Managed, inline, and customer-managed policies are supported.
   - Examples:
     - `s3:PutObject`
     - `ec2:DescribeInstances`


---

IAM permissions play a vital role in securing cloud environments by controlling who can access and perform actions on resources.
