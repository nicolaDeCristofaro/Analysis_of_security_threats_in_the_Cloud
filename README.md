# Analysis of security and privacy threats in the cloud, countermeasures adopted and how the blockchain can help

### Abstract 
The Cloud Computing paradigm is considered one of the most important paradigm shifts, in the technological field, in recent years. Its remarkable growth is mainly due to the opportunity it offers users to reduce costs and at the same time increase the efficiency of applications by providing a new approach to using services. In fact, one of the main features of the Cloud is the ability to pay only for the resources actually used and thus avoid large initial investments. However, despite the numerous advantages offered, there are still possible security threats that are perceived as the main obstacle to the massive adoption of the Cloud. In this study we analyze the main security and privacy threats in the Cloud, and the related countermeasures adopted to achieve a reliable Cloud environment. In particular, we will refer to the security mechanisms used by the most used Cloud Providers: Amazon Web Services and Microsoft Azure. Furthermore, a real case study of an attack on a Cloud Provider will be presented with the relative details to understand the level of associated risk, and finally we will make an overview on the use of the blockchain in combination with the Cloud to understand which added values it manages to achieve.

## Index

### 1. [Introduction on Cloud and Cloud Security](#chap1)
- What is the Cloud in short 
- Some Statistics
- The main benefits of the Cloud

### 2. [Security and Privacy threats in the Cloud](#chap2)
- Introduction to Cloud Security
  - Extensibility & Shared Responsibility
  - Service Level Agreement (SLA)
- Threats Agents
- Outsourcing of data and computation
  - Traffic Eavesdropping
  - Malicious Intermediary
- Denial of Service
- Authentication and Identity Management
  - Insufficient Authorization
- Access Control
- Virtualization & Hypervisor
- Trust Management 
  - Overlapping Trust Boundaries
- Privacy and Data Protection
- Security Policy Disparity
  
### 3. [Countermeasures to Cloud Security Threats](#chap3)
- Encryption + type of encryption used in cloud
- Hashing
- Digital Signature
- Public Key Infrastructure (PKI)
- Identity and Access Management
- Single Sign-on (SSO)
- Cloud-Based Security Groups
- Hardened Virtual Server Images

### 4. [Security services of the main Cloud Providers](#chap4)
- Usage statistics of the main Cloud Providers
- Overview of the mechanisms adopted by AWS (Amazon Web Services)
- Overview of mechanisms adopted by Microsoft Azure
  
### 5. [Analysis of a real case study: attack to Tesla](#chap5)
- Details of the attack
- Impact of the attack
- Preventive mitigation actions
- Investigative mitigation actions
- Corrective mitigation actions

### 6. [Blockchain and Cloud Security](#chap6)
- x
- y

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

Cloud Advantages in short

## 2. Security and Privacy threats in the Cloud <a name="chap2"></a>

#### Introduction to Cloud Security
Although we have seen the potential advantages of the Cloud, its use or rather its adoption is often a source of doubts, especially in contexts where the data processed is particularly sensitive. The reason is that, in addition to the benefits, there are also security and privacy concerns that comes with the use of the Cloud. So, without appropriate security and privacy solutions designed for clouds, this potentially disrupting computing paradigm could become a huge failure. Several surveys of potential Cloud adopters indicate that security and privacy is the primary concern hindering its adoption.

Let's first introduce some security concepts that are specific to the Cloud environment that it is important to be aware of.

- **Extensibility & Shared Responsibility**
Cloud providers and customers must share the responsibility for security and privacy in cloud computing environments, but sharing levels will differ for different Cloud delivery models:
  -
- **Service Level Agreement (SLA)**


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

## 4. Security services of the main Cloud Providers <a name="chap4"></a>

## 5. Analysis of a real case study: attack to Tesla <a name="chap5"></a>

## 6. Blockchain and Cloud Security <a name="chap6"></a>

## 7. Conclusions <a name="conclusions"></a>


**References**:
 
- Thomas Erl, Ricardo Puttini, Zaigham Mahmood, "Cloud computing. Concepts, technology & architecture," 1st edition, Prentice Hall, 2013
- H. Takabi, J. B. D. Joshi and G. Ahn, "Security and Privacy Challenges in Cloud Computing Environments," in _IEEE Security & Privacy_, vol. 8, no. 6, pp. 24-31, Nov.-Dec. 2010, doi: 10.1109/MSP.2010.186.
- Cloud Security Alliance, "Top Threats to Cloud Computing: Egregious Eleven Deep Dive" 09/23/2020
- Introduction to AWS Security - AWS Whitepaper - (https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/introduction-aws-security.pdf)
- Introduction to Azure security - (https://docs.microsoft.com/en-us/azure/security/fundamentals/overview)
- S. Pavithra, S. Ramya and S. Prathibha, "A Survey On Cloud Security Issues And Blockchain," 2019 3rd International Conference on Computing and Communications Technologies (ICCCT), 2019, pp. 136-140, doi: 10.1109/ICCCT2.2019.8824891.
- K. Gai, K. R. Choo and L. Zhu, "Blockchain-Enabled Reengineering of Cloud Datacenters," in IEEE Cloud Computing, vol. 5, no. 6, pp. 21-25, Nov./Dec. 2018, doi: 10.1109/MCC.2018.064181116.



