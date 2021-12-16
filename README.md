# Analysis of security and privacy threats in the cloud, countermeasures adopted and how the blockchain can help

### Abstract 
The Cloud Computing paradigm is considered one of the most important paradigm shifts, in the technological field, in recent years. Its remarkable growth is mainly due to the opportunity it offers users to reduce costs and at the same time increase the efficiency of applications by providing a new approach to using services. In fact, one of the main features of the Cloud is the ability to pay only for the resources actually used and thus avoid large initial investments. However, despite the numerous advantages offered, there are still possible security threats that are perceived as the main obstacle to the massive adoption of the Cloud. In this study we analyze the main security and privacy threats in the Cloud, and the related countermeasures adopted to achieve a reliable Cloud environment. In particular, we will refer to the security mechanisms used by the most used Cloud Providers: Amazon Web Services and Microsoft Azure. Furthermore, a real case study of an attack on a Cloud Provider will be presented with the relative details to understand the level of associated risk, and finally we will make an overview on the use of the blockchain in combination with the Cloud to understand which added values it manages to achieve.

## Index

### 1. [Introduction on Cloud and Cloud Security](#chap1)
- [What is the Cloud in short](#what-is-cloud-in-short)
- [Some Statistics](#some-statistics)
- [The main benefits of the Cloud](#the-main-benefits-of-the-cloud)

### 2. [Security and Privacy threats in the Cloud](#chap2)
- [Introduction to Cloud Security](#introduction-to-cloud-security)
  - Extensibility & Shared Responsibility
- [Threats Agents](#threats-agents)
- [Outsourcing of data and computation](#outsourcing-of-data-and-computation)
  - Traffic Eavesdropping
  - Malicious Intermediary
- [Denial of Service](#denial-of-service)
- [Authentication and Identity Management](#authentication-identity-management)
  - Insufficient Authorization
- [Access Control](#access-control)
- [Virtualization & Hypervisor](#virtualization--hypervisor)
- [Trust Management: Overlapping Trust Boundaries](#overlapping-trust-boundaries)
- [Privacy and Data Protection](#privacy-and-data-protection)
- [Security Policy Disparity](#security-policy-disparity)
  
### 3. [Countermeasures to Cloud Security Threats](#chap3)
- [Encryption](#encryption)
- [Hashing](#hashing)
- [Digital Signature](#digital-signature)
- [Public Key Infrastructure (PKI)](#public-key-infrastructure-pki)
- [Identity and Access Management](#identity-and-access-management-iam)
- [Single Sign-on (SSO)](#single-sign-on-sso)
- [Cloud-Based Security Groups](#cloud-based-security-groups)
- [Hardened Virtual Server Images](#hardened-virtual-server-images)

### 4. [Security services of the main Cloud Providers](#chap4)
- [Usage statistics of the main Cloud Providers](#usage-statistics-of-the-main-cloud-providers)
- [Overview of the security mechanisms adopted by AWS (Amazon Web Services)](#overview-of-the-security-mechanisms-adopted-by-aws-amazon-web-services)
- [Overview of the security mechanisms adopted by Microsoft Azure](#overview-of-the-security-mechanisms-adopted-by-microsoft-azure)
  
### 5. [Analysis of a real case study: attack to Tesla](#chap5)
- [Attack Details](#attack-details)
- [Technical Impacts](#technical-impacts)
- [Business Impacts](#business-impacts)
- [Preventive mitigation actions](#preventive-mitigation)
- [Detective mitigation actions](#detective-mitigation)
- [Corrective mitigation actions](#corrective-mitigation)

### 6. [Blockchain and Cloud Security](#chap6)
- [What is blockchain technology?](#what-is-blockchain-technology)
- [Where blockchain technology comes handy?](#where-blockchain-technology-comes-handy)
- [Blockchain security and Cloud Computing](#blockchain-security-and-cloud-computing)
  - Blockchain-as-a-Service (BaaS)
  - Blockchain-enabled Data Provenance in Cloud
  - Blockchain-based Access Control in Cloud
  - Cloud Computation Offloading for Blockchain
  - Cloud Storage Offloading for Blockchain
  - Cloud Hardware for Blockchain mining

### 7. [Conclusions](#conclusions)


## 1. Introduction on Cloud and Cloud Security <a name="chap1"></a>


#### What is Cloud in short
The US National Institute of Standards and Technology (NIST) defines the Cloud as follows:

*"Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction".*

#### Some statistics
According to predictions from Gartner, global spending on cloud services is expected to reach over $482 billion in 2022, up from $313 billion in 2020. Cloud computing infrastructure is the backbone of the delivery pipeline of just about every digital service, from social media and streaming entertainment to connected cars and autonomous internet of things (IoT) infrastructure. New or upcoming ultra-fast networks like 5G and Wi-Fi 6E don't just mean more data will be streamed from the cloud; they mean new types of data can be streamed. We see this with the explosion in the availability of cloud gaming platforms such as Google's Stadia and Amazon Luna, which will see increasing levels of investment over the course of 2022. We will also see the arrival of cloud virtual and augmented reality (VR/AR) which should lead to smaller and cheaper headsets. Cloud technology essentially makes every other technology lighter, faster, and more accessible from a customer point of view, and this fact will be a key driver in the migration of more services to cloud platforms.

![Eurostat](./images/Use_of_cloud_computing_services,_2020_and_2021.png)

- Significant differences can be observed across countries in this Eurostat graph. In Sweden (75 %), Finland (75 %), the Netherlands (65 %) and Denmark (65 %) at least 65 % of enterprises used cloud computing. On the other hand, in Greece (22 %), Romania (14 %) and Bulgaria (13 %) less than 25 % of enterprises did so.
- 42 % of EU enterprises used cloud computing in 2021, mostly for hosting their e-mail systems and storing files in electronic form.
- 73 % of those enterprises used sophisticated cloud services relating to security software applications, hosting enterprise’s databases or computing platform for application development, testing or deployment.
- Compared with 2020, the use of cloud computing increased by 6 percentage points.

#### The main benefits of the Cloud
We can therefore see that even if in different proportions the Cloud is widespread and used in every part of the world. This is due to the great advantages that the cloud offers, which we summarize below:

- **Reduced initial investment**: similar to a product wholesaler who buys wholesale goods at lower prices, public cloud providers base their business model on the mass acquisition of IT resources which are then made available to cloud consumers at advantageous prices. This opens the door for organizations to gain access to a powerful infrastructure without having to purchase it themselves.

The most common economic reason for investing in cloud-based IT resources is the reduction or permanent elimination of initial IT investments, i.e. initial hardware and software purchases. This elimination or minimization of initial financial commitments allows companies to start small and consequently increase the allocation of IT resources as needed.
Furthermore, the reduction of the initial capital allows to redirect the capital towards other core areas of the business.

Other benefits related to cost reduction are:
  - On-demand access to short-term pay-as-you-go computing resources (such as hourly processors) and the ability to release these computing resources when they are no longer needed.
  - The perception of having unlimited processing resources available on demand, thus reducing the need for in-depth capacity planning.
  - The ability to add or remove IT resources at a fine-grained level, for example by changing available storage disk space in single gigabyte increments.
  - Infrastructure abstraction so that applications are not stuck in devices or locations and can be easily moved if needed.

- **Increased Scalability**: Cloud platforms allow you to instantly and dynamically allocate IT resources, on demand. This allows cloud consumers to scale their cloud-based IT resources to meet fluctuations and processing spikes automatically or manually. Likewise, cloud-based IT resources can be released (automatically or manually) as processing demands decrease.

- **Increased Availability and Reliability**: By leveraging cloud environments to make IT resources highly available and reliable, organizations are able to increase customer service quality guarantees and further reduce or avoid potential business losses arising from unexpected runtime errors.

In particular:
  - An IT resource with higher availability is accessible for longer periods of time (for example, 22 hours on a 24 hour day). Providers generally offer "resilient" IT resources for which they can guarantee high levels of availability.
  - A more reliable IT resource can avoid and recover exceptional failure situations. The modular architecture of cloud environments provides extensive failover support that increases reliability.

It is important for organizations to carefully review the SLAs offered by cloud service providers when considering leasing cloud-based services and IT resources.

## 2. Security and Privacy threats in the Cloud <a name="chap2"></a>

#### Introduction to Cloud Security
Although we have seen the potential advantages of the Cloud, its use or rather its adoption is often a source of doubts, especially in contexts where the data processed is particularly sensitive. The reason is that, in addition to the benefits, there are also security and privacy concerns that comes with the use of the Cloud. So, without appropriate security and privacy solutions designed for clouds, this potentially disrupting computing paradigm could become a huge failure. Several surveys of potential Cloud adopters indicate that security and privacy is the primary concern hindering its adoption.

Let's first introduce some security concepts that are specific to the Cloud environment that it is important to be aware of.

- **Extensibility & Shared Responsibility**
Cloud providers and customers must share the responsibility for security and privacy in cloud computing environments, but sharing levels will differ for different Cloud delivery models where a cloud delivery model represents a specific combination of IT resources offered by a Cloud Provider:
  - With **SaaS (Software as a Service)**, the Cloud provider manages both the software and the underlying infrastructure. Users access the service over the Internet, usually through a web browser. In this scenario, the Cloud Provider is more responsible for the security and privacy of application services.
  - **PaaS (Platform as a Service)** represents a "ready to use" environment that typically includes IT resources already configured and deployed. PaaS is designed to make application development quick and easy, without the worry of setting up and managing the underlying infrastructure of servers, storage, networks, etc. Obviously, this way you more control of resources than in SaaS but not the full control. Thus, customers are primarly responsible for protecting the applications they build and run on the platform. Providers are then responsible for isolating the customers' applications and workspaces from one another.
  - The **IaaS (Infrastructure as a Service)** model represents a self-contained IT environment composed of infrastructure-centric IT resources, accessible and fully managed by the consumer cloud. This environment can include hardware, networking, connectivity, and other "raw" IT resources. In this scenario It is expected that the consumers secure the operating systems, applications, and content. The Cloud Provider still must provide some basic, low-level data protection capabilities.

#### Threats Agents
Before moving on to analyze the various Cloud security issues, we can distinguish the types of attackers:

- **Anonymous Attacker**: An anonymous user, consumer of cloud services with no permissions in the cloud. It typically exists as an external software program that launches network-level attacks across public networks. Anonymous attackers often resort to committing acts such as bypassing user accounts or stealing user credentials, using methods that ensure anonymity.

- **Malicious Service Agent**: A malicious service agent is able to intercept and forward network traffic flowing within a cloud. It typically exists as a program that pretends to be a service agent with malicious logic. It can also exist as an external program that can remotely intercept and potentially corrupt the message content.

- **Trusted Attacker**: A trusted attacker shares IT resources in the same cloud environment as the cloud consumer and attempts to exploit legitimate credentials to target cloud providers with whom they share IT resources (*Attack from the inside*). Unlike anonymous attackers (who are not "trusted"), trusted attackers usually launch their attacks from inside the trusted boundaries of a cloud by abusing legitimate credentials or by stealing sensitive and confidential information. Examples: weak authentication processes, breaking of a cryptographic mechanism, DDoS ...

- **Malicious Insider**: These are usually human insiders, at the cloud service provider. They are typically current or former employees or third parties with access to the cloud provider's premises. This type of threat agent carries enormous potential for harm, as the malicious insider may have administrative privileges to access the IT resources of cloud consumers.

Now we can go into the details of the problems and threats of the Cloud, then in the next chapter we will provide the relative countermeasures adopted.

#### Outsourcing of data and computation
Cloud computing provides access to data, but the challenge is to ensure that only authorized entities can gain access to it. When we use cloud environments, we rely on third parties to make decisions about our data and platforms in ways never seen before in computing. It’s critical to have appropriate mechanisms to prevent cloud providers from using customers’ data in a way that hasn’t been agreed upon.

Examples of attacks in this category could be:
  - **Traffic Eavesdropping**: Traffic interception occurs when data transferred within a cloud (usually from the consumer to the cloud provider) is passively intercepted by a malicious service agent for illegitimate information-gathering purposes. The purpose of this attack is to directly compromise the confidentiality of the data and, possibly, the confidentiality of the relationship between the consumer and the cloud provider. Due to the passive nature of the attack, it can more easily go unnoticed for long periods of time.
  - **Malicious Intermediary**: This type of threat occurs when messages are intercepted and altered by a malicious service agent, thus potentially compromising the confidentiality and / or integrity of the message. It can also insert malicious data into the message before forwarding it to its destination.

#### Denial of Service
The goal of the Denial of Service (DoS) attack is to overload IT resources to the point where they cannot function properly. This form of attack is commonly launched in one of the following ways:
- The workload on cloud services has artificially increased with imitation of messages or repeated communication requests.
- The network is overloaded with traffic to reduce its responsiveness and paralyze its performance.
- Multiple requests for cloud services are sent, each of which is designed to consume excessive memory and processing resources.
  
Successful DoS attacks result in server degradation and / or failure.

#### Authentication, Identity Management 
The conventional and the easiest way of authentication for a user that wants to use cloud services, is via password, something that is shared between the user and the authentication service and is, ideally, both secret and hard to guess. Identity management systems are responsible for the storage, management and secure transmission of user ID and password to the authentication service for verification. 

In a common Cloud hosted web-service access scenario, user enters his user ID and password to prove his identity to the authentication server. However, this mechanism is the least secure authentication mechanism for the dynamic Cloud environment that is susceptible to replay attack and identity theft since user passwords can easily be stolen. Other reasons might include sharing of passwords or usage of overly simplistic passwords among many others.

An example of attack in this category is:
  - **Insufficient Authorization**
    - This attack occurs when access is granted to an attacker incorrectly or with too wide privileges, resulting in the attacker gaining access to IT resources that are normally protected. A variant of this attack, known as Weak Authentication, can occur when weak passwords or shared accounts are used.

#### Access Control
In many application scenarios, such as those in enterprises or organizations, users’ access to data is usually selective and highly differentiated. Different users enjoy different access privileges with regard to the data. When data are outsourced to the cloud, enforcing secure, efficient, and reliable data access among a large number of users is thus critical. 

Traditionally, to control the dissemination of privacy-sensitive data, users establish a trusted server to store data locally in clear, and then control that server to check whether requesting users present proper certification before letting them access the data. From a security standpoint, this access control architecture is no longer applicable when we outsource data to the cloud. Because data users and cloud servers aren’t in the same trusted domain, the server might no longer be fully trusted as an omniscient reference monitor9 for defining and enforcing access control policies and managing user details. In the event of either server compromise or potential insider attacks, users’ private data might even be exposed.

#### Virtualization & Hypervisor
Virtualization is an important enabling technology that helps abstract infrastructure and resources to be made available to clients as isolated VMs. A hypervisor or VM monitor is a piece of software that lets multiple operating systems run on a host computer concurrently. 

In other words, the virtualization and hypervisor combination provides multiple cloud users with access to IT resources that share the underlying hardware but are logically isolated from each other.

Although this provides a means to generate virtualized resources for sharing, such technology’s presence also increases the attack surface. We need mechanisms to ensure strong isolation, and secure communications between VMs.

An example of attack in this category is:
- **Virtualization Attack**
  - As cloud providers grant cloud consumers administrative access to virtualized IT resources (such as virtual servers), there is an inherent risk that cloud consumers may abuse this access to attack underlying physical IT resources. A Virtualization Attack exploits vulnerabilities in the virtualization platform to compromise its confidentiality, integrity and / or availability.A successful virtualization attack can have significant repercussions on all other users who use virtualized resources on the attacked physical hardware.

#### Overlapping Trust Boundaries
If physical IT assets within a cloud are shared by multiple consumers of cloud services, we say these consumers have overlapping boundaries of trust.

Malicious cloud consumers can target shared IT resources with the intention of compromising other consumers. The consequence is that some or all of the other consumers of cloud services could be affected by the attack and the attacker could use virtual IT resources of users with whom they share the same border of trust.
  
### Privacy and Data Protection
Privacy is a core issue in all the challenges we’ve discussed so far.. Many organizations aren’t comfortable storing their data and applications on systems that reside outside of their on-premise datacenters. This might be the single greatest fear of cloud clients. By migrating workloads to a shared infrastructure, customers’ private information faces increased risk of potential unauthorized access and exposure. 

Cloud service providers must assure their customers and provide a high degree of transparency into their operations and privacy assurance. Privacy-protection mechanisms must be embedded in all security solutions. 

In a related issue, it’s becoming important to know who created a piece of data, who modified it and how, and so on. Provenance information could be used for various purposes such as traceback, auditing, and history-based access control. Balancing between data provenance and privacy is a significant challenge in clouds where physical perimeters are abandoned.

#### Security Policy Disparity
When a cloud consumer entrusts IT resources to a public cloud provider, they may have to accept that their traditional approach to information security may not be identical or even similar to that of the cloud provider.

Even when hiring IT resources based on raw infrastructure, the cloud consumer may not be granted sufficient administrative control or influence over the security policies that apply to the cloud provider's IT resources.

This is mainly due to the fact that these IT assets are still legally owned by the cloud service provider and continue to fall under its responsibility. Additionally, with some public clouds, additional third parties, such as security brokers and certification authorities, can introduce their own distinct set of security policies and practices, further complicating any attempt to standardize the protection of cloud consumers' resources.

## 3. Countermeasures to Cloud Security Threats <a name="chap3"></a>
What techniques are used as countermeasures to the vulnerabilities in the Cloud identified in the previous section? Here are some of them:

#### Encryption

The data, by default, is in a human-readable format known as plain text. When transmitted over a network, plaintext is vulnerable to unauthorized and potentially harmful access. The encryption mechanism is a digital encryption system dedicated to preserving the confidentiality and integrity of the data. It is used to encode plain text data in a secure format that is unreadable by unauthorized users.

Encryption technology commonly relies on a standardized algorithm called a cipher to transform the original plaintext data into encrypted data, referred to as ciphertext.

The data is associated with a character string called an encryption key, a secret message established and shared between authorized parties. The encryption key is used to decrypt the ciphertext into its original plaintext format.

The encryption mechanism can help counter cloud security threats such as:
- Traffic eavesdropping
- malicious intermediaries
- insufficient authorization
- overlapping trust boundaries
 
There are two common forms of encryption known as symmetric encryption and asymmetric encryption.

I won't go into the details of both techniques, but we can say that the basic difference between these two types of encryption is that symmetric encryption uses one key for both encryption and decryption, and the asymmetric encryption uses public key for encryption and a private key for decryption.

#### Hashing
The hashing mechanism is used when a one-way, non-reversible form of data protection is required. Once hashing has been applied to a message, it is blocked and no key is given to unlock the message. **A common application of this mechanism is the storage of passwords.**

Hashing technology can be used to derive a hashing code or digest from a message, which is often of a fixed length and smaller than the original message. The sender of the message can then use the hashing mechanism to attach the message digest to the message.

The recipient applies the same hash function to the message to verify that the digest of the produced message is identical to the one that accompanied the message. Any modification to the original data results in a completely different message digest and clearly indicates that a tamper has occurred.

In addition to its use to protect stored data, cloud threats that can be mitigated by the hashing mechanism include

- malicious intermediaries
- insufficient authorization

#### Digital Signature

The digital signature mechanism is a means of providing authenticity and data integrity through authentication and non-repudiation. A message is digitally signed before transmission, which is then rendered invalid if the message undergoes subsequent unauthorized modification. 

A digital signature provides proof that the received message is the same as the one created by its legitimate sender.

Both hashing and asymmetric encryption are involved in creating a digital signature, which essentially exists as a digest of the message that has been encrypted by a private key and appended to the original message.

The recipient verifies the validity of the signature and uses the corresponding public key to decrypt the digital signature, which produces the message digest. The hashing mechanism can also be applied to the original message to produce this digest message. Identical results from the two different processes indicate that the message has maintained its integrity.
 
The digital signature mechanism helps mitigate security threats
- malicious intermediaries
- insufficient authorization
- overlapping trust boundaries

#### Public Key Infrastructure (PKI)
A common approach to managing asymmetric key issuance is based on the Public Key Infrastructure (PKI) mechanism, which exists as a system of protocols, data formats, rules and practices that allow systems to use securely public key cryptography.

This system is used to bind public keys to their respective key owners (known as public key identification) while allowing verification of the validity of the key. PKIs rely on the use of digital certificates, which are digitally signed data structures that bind public keys to the identities of the certificate owner, as well as related information, such as validity periods.

Digital certificates are typically digitally signed by a third-party certification authority (CA).

Larger organizations, such as Microsoft, can act as their own CA and issue certificates to their customers and the public, as individual users can also generate certificates as long as they have the appropriate software tools.

Threats mitigated:
- insufficient authorization

#### Identity and Access Management (IAM)
This mechanism includes the components and policies needed to control and track user identities and access privileges for IT systems, environments and resources.

Specifically, IAM mechanisms exist as systems composed of four main components:

- **Authentication**: Username and password combinations remain the most common forms of user authentication credentials managed by the IAM system, which can also support digital signatures, digital certificates, biometric hardware, and so on. We can say this component tries to respond the question WHO ARE YOU?.
  
- **Authorization**: Defines the correct granularity for access and privilege controls. It respond to the question WHAT CAN YOU DO?

- **User Management**: The user management program is responsible for creating new users and access groups (each cloud consumer can have several associated users with relative privileges), resetting passwords, defining password policies and managing privileges.

- **Credential Management**: The credential management system establishes the identities and access control rules for defined user accounts.

Although the objectives are similar to those of the PKI mechanism, the scope of implementation of the IAM mechanism is distinct because its structure includes access controls and policies as well as the assignment of specific levels of user privileges.

Threats mitigated:
- insufficient authorization
- overlapping trust boundaries
- DDoS

#### Single Sign-On (SSO)
Propagating authentication and authorization information for a consumer cloud across multiple cloud services can be a challenge, especially if you need to invoke multiple cloud services as part of the same overall runtime task.

The Single Sign-on (SSO) mechanism allows cloud consumer to be authenticated by a security broker, which establishes a security context that is maintained while the cloud services consumer accesses other cloud services.

Otherwise, the consumer of the cloud service would have to re-authenticate with each subsequent request.

The credentials initially provided by the cloud service consumer remain valid for the duration of a session, while their security context information is shared.

The SSO mechanism security broker is particularly useful when a consumer of cloud services needs to access cloud services that reside on different clouds.

* This mechanism does not counteract any of the cloud threats we have seen, but mainly improves usability in accessing and managing cloud resources.*

#### Cloud-Based Security Groups
Cloud resource segmentation is accomplished which is a process by which separate physical and virtual IT environments are created for different users and groups. For example, an organization's WAN can be partitioned based on individual network security requirements. One network can be established with a resilient firewall for external Internet access, while a second is implemented without a firewall because its users are internal and cannot access the Internet.

The cloud-based resource segmentation process creates security groups determined by security policies. Networks are segmented into security groups that form the logical network perimeters. Each cloud-based IT resource is assigned to at least one security group.

Each security group is assigned specific rules that govern communication between security groups. For example, multiple virtual servers running on the same physical server can become members of different security groups.

Virtual servers can be further separated into public-private groups, dev-production groups, or any other designation configured by the cloud resource administrator.

Threats mitigated:
- Unauthorized access to cloud resources
- overlapping trust boundaries
- insufficient authorization
- DDoS

#### Hardened Virtual Server Images
A virtual server in the Cloud is created from a template configuration called a *virtual server image*.

Hardening virtual server image is the process of removing unnecessary software from a system to limit potential vulnerabilities that can be exploited by attackers. Removing redundant programs, closing unnecessary server ports, and disabling unused services, internal root accounts, and guest access are all examples of hardening.

A secure virtual server image is a template for creating virtual server instances that has undergone a hardened process. This generally results in a virtual server template that is significantly more secure than the original standard image.

Threats mitigated:
- overlapping trust boundaries
- insufficient authorization
- DDoS
  
## 4. Security services of the main Cloud Providers <a name="chap4"></a>

#### Usage statistics of the main Cloud Providers
Cloud adoption continues to increase as agile development, rapid deployment, and unlimited scale become the new normal for customers of all industries, sizes, and geographies. In Gartner's 2021 evaluation covering both cloud infrastructure and platform services (IaaS & PaaS, or "CIPS"), AWS is evaluated as a Leader placed highest in both axes of measurement, Ability to Execute and Completeness of Vision.

<img src="./images/Figure_1_Magic_Quadrant_for_Cloud_Infrastructure_and_Platform_Services.png">

Below we analyze the security mechanisms of the two most used Cloud Providers: Amazon Web Services (AWS) and Microsoft Azure.

#### Overview of the security mechanisms adopted by AWS (Amazon Web Services)
We can distinguish the different security services provided by AWS into categories. For each of them some security service will be explained. For the details go to the links in references.

- #### Infrastructure protection

- #### Data Protection and Encryption

- #### Identity and Access Management

- #### Incidence response

- #### Monitoring and Logging

- #### Compliance


#### Overview of the security mechanisms adopted by Microsoft Azure
Also for Microsoft Azure we present an overview of some of the security services offered divided into categories.

While in AWS the categories were organized by the type of security offered, here the categories are organized by the cloud infrastructure components to be secured.

- #### Operations

- #### Applications

- #### Storage

- #### Networking

- #### Compute


## 5. Analysis of a real case study: attack to Tesla <a name="chap5"></a>
This is a real-world case study attack.and breaches cited in the Top Threats Deep Dive for its foundation. We'll provide an attack-style synopsis of the actor spanning from threats and vulnerabilities to end controls and mitigations.

#### Attack Details
- **Actor**: *External malicious hacker(s)* gained access to an unsecured Kubernetes administrative interface. This was discovered by security researchers and reported to Tesla.
  
- **Attack**: The attackers gained access to AWS access credentials via the unsecured Kubernetes administrative interface. These credentials further provided access to S3 buckets containing non-public vehicle telemetry data. In addition, the attackers installed mining scripts on the hijacked Kubernetes instance to mine cryptocurrency.
  
- **Vulnerabilities**: Misconfiguration of secure authentication mechanisms within the Kubernetes console provided access to confidential data including credentials.
  - Insufficient credential management and effective encryption measures possibly facilitated lateral movement across the network.
  - Inadequate antimalware and security monitoring failed to detect and prevent the installation of mining scripts.

#### Technical Impacts
- **Data Breach**: The attackers were able to gain access to AWS S3 buckets housing intellectual property related to internally-used engineering test cars.
- **Malware infection**: The intrusion allowed the attackers to install evasive cryptocurrency mining scripts. In addition to steaking computing resources, these nefarious scripts provide an avenue for attackers to persist within the environment if not properly detected and remediated

#### Business Impacts
- **Financial**: Possible increases in the cost of cloud computing resources could be realized depending on the length of time the attackers spent mining crypto currency within the compromised network: possible risk of exfiltrating and selling valuable intellectual property to highest bidding competitor.
- **Operational**: Time and effort taken by the Digital Forensic and Incident Response (DFIR) team to manage malware infections, revoke access credentials and ensure reconfiguration of the Kubernetes administrative instance.
- **Compliance:** This attack may not have direct impacts from non compliance since confidential data such as customer PII was not exposed. However, there was a loss of confidentiality of sensitive data that could be possibly related to trade secrets.
- **Reputational**: The data breach may have led to a reduction of consumer confidence and a diminished perception of brand value.

#### Preventive Mitigation
- **Unauthorized Software Installations** – Organizations should have application whitelisting policies in place to restrict the installation of unauthorized software (including malware) on end-points and servers.
- **Sensitive Data Protection** – Encryption should be enforced for sensitive data in stored in the cloud. CSPs should provide customers with the option to select client side or server-side encryption. Where possible, customers should select encryption mechanisms that complement the value and use of data being protected.
- **Credential Lifecycle/Provision Management** – Establishment of user access control policies supporting business processes and technical controls that ensure appropriate identity and access management for all users with access to data.
- **Employee training** – Intelligence driven security awareness training should be provided to DevOps teams on secure development practices. This can help mitigate the risk of security misconfiguration.
- **Vulnerability / Patch Management** – Timely detection of weaknesses within configurations of applications, infrastructure, network and system components can ensure efficacy of implemented security controls. For example, penetration testing of applications can reveal the presence of weak authentication mechanisms that need to be corrected before being exploited by attackers.

#### Detective Mitigation
- **Quality Testing** – Organizations should have defined change control and testing processes to test applications and before being deployed into production. This can help in detecting misconfigured services that can affect the confidentiality, integrity and availability of systems and services.
- **Audit Logging / Intrusion Detection** – CSP’s should provide customer’s the capability to detect potentially suspicious network behaviours/ anomalies within their environment. Furthermore, the CSP needs to ensure the confidentiality, integrity and availability of audit logs are maintained at all times to aid forensic investigations.
- **Anti-Virus / Malicious Software** – Some endpoint detection and response (EDR) solutions are capable of detecting and mitigating the effects of malware intrusions. Although not fully encompassing, these solutions at the very least can help in detecting and preventing the execution of commodity malware or publicly known tools which are still currently being used in the wild by adversaries.
  

#### Corrective Mitigation
- **Incident Management** – An Incident Response Team will be required to triage/investigate suspicious security events and ensure timely and thorough management of incidents, as established within the Incident Response process.
- **Incident Response Metrics** – Each incident should be tracked in order to provide justification for time and resources spent to manage incidents. This will aid Management in making investment decisions needed to improve the Incident Response process.


## 6. Blockchain and Cloud Security <a name="chap6"></a>

#### What is blockchain technology?
The concept of blockchain gained mainstream attention in 2017. In simple terms, blockchain is a technology that enables data to be stored and transferred on a peer-to-peer basis. It can also be compared to a bank ledger holding transactions. It stores information about date, time, and amount of money, etc. It’s used in a ‘decentralised’ manner and it eliminates the need for ‘trusted third parties’. The blockchain network doesn’t have any central authority.

A particular property of the blockchain is: *"The data structure in a blockchain is append-only: the data cannot be modified or deleted"*.

#### Where blockchain technology comes handy?
The modern digital economy is based on reliance on a certain trusted authority. Simply put, the online transactions we make rely on trusting someone to tell us the truth. For example, when we send an email to somebody we need the provider to tell us that the email is delivered. The point is that we live our life rather uncertainly in the digital world by relying on a third entity for the security of our digital assets. The bad news is that these so-called third-party sources can be infiltrated.

Blockchain technology has the extensive potential to fundamentally transform the digital world by facilitating a distributed consensus. It means that every single transaction, whether be it past and present, including digital assets, can be checked at any time in the future. Better yet, it implements this without compromising the security of digital assets.

#### Blockchain security and Cloud Computing
Fusing blockchain technology with existing cloud system has a great potential in both functionality/performance enhancement and security/privacy improvement. The question remains on how can we use blockchain and cloud computing for additional value creation? How blockchain technology inserts into current deployed cloud solutions and enables the reengineering of cloud datacenter?

Below we analyze some aspects that link blockchain to cloud computing. We can summarize them in this scheme:

- #### Blockchain-as-a-Service (BaaS)
  BaaS is a type of blockchain service model that allows blockchain systems or components to be computing resource that can be used for supporting cloud systems or other applications. The major intention of using BaaS is allowing customers to focus on core business rather than struggling with technical obstacles of blockchain. The basic idea of BaaS is that the blockchain network/application is treated as a service offering, on which users are allowed to configure blockchain settings, such as blockchain network types and smart contract rules. Infrastructure for establishing blockchain network is offered by the service provider and partial codes of blockchain are available for open source. 
  
  For instance Microsoft Azure supports Ethereum, Corda and Hyperledger Fabric for the deployment and configuration of a blockchain network. The Azure’s user only needs configure certain parameters rather than figuring out all technical details. Amazon Web Services (AWS), also, has provided BaaS in their mature and widely-used cloud environment since 2016. AWS’s BaaS can support both Ethereum and Hyperledger.

  In most current blockchain systems, an assumption was made that the demand of the trustful third-party was reduced due to the decentralization setting. Interactions between stakeholders were assumed to be secure no matter whether the stakeholder was trustful. This assumption could be challenged and there could be trust management issues in BaaS because inserting service providers into the blockchain system could cause **"recentralizations"**. One of the reasons was that the service provider could be or had connections with stakeholder(s) so that the blockchain offering might lack of trust. A potential solution was signing a service agreement to restrict activities of CSPs (Cloud Service Providers).

- #### Blockchain-enabled Data Provenance in Cloud
  *Provenance* refers to a type of metadata that records and describes operation data. In the scenario of cloud computing, a functional provenance tells **when, where and how** data are stored, accessed, modified and deleted in cloud datacenter.
  
  The application of provenance in cloud benefits both CSPs and users. To address providers’ demands, provenance metadata could be utilized to debug, for discovering potential security vulnerabilities,  assist CSPs to identify abnormal process in clouds, e.g., unexpected running applications, which continually consuming resources and so on. On the other hand, from the perspective of users, provenance can protect users data from the threat of malicious insiders and also provides a platform with a function of recording both administrative and malicious operations. A long-run of fulfillment of Service Level Agreement (SLA) can be monitored under the restriction of provenance information.
  
  Benefits of provenance as discussed above are based on the assumption of metadata that were secure and reliable. However, provenance records still had a chance to be tempered by the threat agent, which could disable/misuse the provenance system.

  **As a temper-resistant distributed ledger, blockchain could ensure the security of provenance data.** The basic idea of blockchain-based data provenance is using blockchain’s characteristic in traceability to record each activity happened to data on blocks.

- #### Blockchain-based Access Control in Cloud
  Access control was an essential method to provide cloud data security and privacy, which kept cloud data from intrusive and unauthorized users. Traditional access control methodologies in clouds were based on well-established access control policies. An example could be DAC (Discretionary Access Control) where the legitimate user (e.g., service provider) was responsible for determining how other users access to objects (e.g., cloud users).

  In any case, common weakness of traditional access control mechanisms is that they highly rely on a centralization settings, which generally lacks transparency, traceability, tamper-resistance, and multi-party governance.

  Differing from traditional access control methods, **Blockchain-based Access Control (BAC)** has a few benefits deriving from characteristics of blockchain. First, BAC introduces consensus into the operation of access control, such that, logically speaking, all stakeholders can be involved during the process. Establishing a consensus generally needs an agreement-level consent made by participant voters or deciders, which strengthens the security from the perspective of the decentralization. Second, traceability supported by blockchain provides a traceable and immutable governance capability for access control.

  A decentralized access control technology powered by blockchain could avoid the risk of single point failure and data misusing caused by third-parties. By applying blockchain technology, data owners could flexibly and completely control the access of their own data.

  To conclude, traditional access control methods face challenges in single point failure, unreliable trusted third parity and lack of user’s control. By implementing blockchain technology, users could fully control their data without threat of single point failure. In addition, smart contract provided automatic access management as well as detection and punishment of misbehaviors.
  
- #### Cloud Computation Offloading for Blockchain
  Despite benefits of blockchain system in security, transparency and fault-tolerance, blockchain-based applications frequently needed a powerful backend service supports. Most blockchain systems utilized PoW consensus. Since the invention of Bitcoin, PoW had been a major consensus mechanism in blockchain system. In PoW mechanism, miners scramble the right of packaging block by solving a cryptographic puzzle. Although PoW provides high fault tolerance and security, it is computational exhausted to each node in the blockchain network. Portable communication devices, such as mobile smart phone, could not be deployed by PoW blockchain due to its constrained computation ability. Outsourcing this cryptographic puzzle game can be a solution in this scenario. 

- #### Cloud Storage Offloading for Blockchain
  Although blockchain was capable of storing temper-resistant data on-chain, blockchain’s storage capability was limited. For example, Bitcoin’s block size was only 1MB, which cannot used to storage large volume of data. Meanwhile, storing high amount of data on-chain could lead the full node size of the blockchain network intolerable high to PC and mobile users. Thus, off-chain storage technology was introduced to tackle this challenge. Cloud service Providers offer storage-as-a-service as a scalable off chain solution to users.

  Using cloud storage is an alternative method for reinforcing blockchain systems, from the perspective of mass data storage, which reduces the restriction caused by the limited storage space of blocks. 
  
  The crucial issue is to determine which data shall be stored in blocks in order to retrieve a great balance between block size and blockchain functionality. 
  
  Another aspect is using blockchain techniques to facilitate secure data sharing, e.g., healthcare. In the paper of reference it is pointed out the potential hazard caused by centralized data storage and demonstrated a blockchain-based data sharing for securing personal health data.

  Sun et al. in the study reported in the references, applied off-chain technology to store high amount of EHR (Electronic Health Records) data. In this work, EHR data address was stored on-chain, while the EHR data were encrypted and saved in data owner’s off-chain database. During the sharing process, the data owner firstly signed the EHR data’s address with his attributes. Then the signed address was stored in the blockchain transactions. Users verify the data owner’s signature when retrieving the data.

- #### Cloud Hardware for Blockchain mining
  Increasing difficulties during the blockchain mining process made on-premises deployment of miners expensive and space-consuming. Due to the development of parallel computing, cloud could be a flexible, pay-as-you-go manner with high computation performance. 
  
  Differing from traditional blockchain mining, cloud-based mining had an observable advantage. The merit was caused by the centralization setting of clouds, such that both energy saving and efficiency performance could be improved due to the hardware resource optimization. Cloud data center’s processing unit’s computation ability fundamentally determined its PoW executing efficiency.

  There are different cloud mining hardware generation. CPU-based mining was original approach. It provided fully decentralization during PoW consensus but the most used It is maybe GPU miner, though energy costly, offered high amount of hashrate.

## 7. Conclusions <a name="conclusions"></a>
Security and privacy are certainly the main obstacles to the massive adoption of the Cloud. Being aware of the main problems and threats allows Cloud Consumers on one hand to carefully manage their share of responsibility and, on the other hand, allows Cloud Providers to develop their services by giving increasing importance to security.

Making the Cloud environment a safe and trustworthy environment will allow an increasing number of users to be able to take advantage of the many benefits it offers and therefore allow the realization of ideas and projects that without the Cloud would not have seen a positive conclusion, perhaps at due to large initial investments that the Cloud avoids.

**References**:
 
- Thomas Erl, Ricardo Puttini, Zaigham Mahmood, "Cloud computing. Concepts, technology & architecture," 1st edition, Prentice Hall, 2013
- H. Takabi, J. B. D. Joshi and G. Ahn, "Security and Privacy Challenges in Cloud Computing Environments," in _IEEE Security & Privacy_, vol. 8, no. 6, pp. 24-31, Nov.-Dec. 2010, doi: 10.1109/MSP.2010.186.
- Cloud Security Alliance, "Top Threats to Cloud Computing: Egregious Eleven Deep Dive" 09/23/2020
- Introduction to AWS Security - AWS Whitepaper - (https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/introduction-aws-security.pdf)
- Cloud Security, Identity and Compliance Products - Amazon Web Services - (https://aws.amazon.com/products/security/)
- Introduction to Azure security - (https://docs.microsoft.com/en-us/azure/security/fundamentals/overview)
- K. Gai, K. R. Choo and L. Zhu, "Blockchain-Enabled Reengineering of Cloud Datacenters," in IEEE Cloud Computing, vol. 5, no. 6, pp. 21-25, Nov./Dec. 2018, doi: 10.1109/MCC.2018.064181116.
- K. Gai, J. Guo, L. Zhu and S. Yu, "Blockchain Meets Cloud Computing: A Survey," in IEEE Communications Surveys & Tutorials, vol. 22, no. 3, pp. 2009-2030, thirdquarter 2020, doi: 10.1109/COMST.2020.2989392.



