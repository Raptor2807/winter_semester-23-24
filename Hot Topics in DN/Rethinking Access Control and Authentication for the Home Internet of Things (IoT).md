_written_ by : Weijia He, Maximilian Golla† , Roshni Padhi, Jordan Ofek,
Markus Dürmuth† , Earlence Fernandes‡ , Blase Ur
University of Chicago, † Ruhr-University Bochum, ‡ University of Washington

### Abstract
This paper addresses the challenges of access control and authentication in the context of the Internet of Things (IoT), where multiple users with intricate social relationships interact with a single device. The current methods are deemed inadequate for providing usable access control specifications in such settings. The proposed reenvisioning suggests a shift towards focusing on IoT capabilities (specific actions devices can perform) rather than a per-device granularity.

Key points from the paper include:

1. **Focus on IoT Capabilities:**
   - The proposal advocates for access control to concentrate on IoT capabilities, emphasizing specific actions that devices can execute.

2. **User Study Insights:**
   - A 425-participant online user study revealed significant variations in participants' desired access control policies for different capabilities within a single device. These preferences also differed based on the user attempting to use a specific capability.

3. **Default Policies:**
   - From the identified desired policies, the paper suggests potential candidates for default policies, considering the diverse preferences observed among users.

4. **Primitives for Complex Policies:**
   - The paper identifies necessary primitives for specifying more complex access control policies. These range from factors like the time of day to the current location of users.

5. **Authentication Methods:**
   - The discussion extends to evaluating the extent to which different authentication methods align with and potentially support the desired access control policies.

The overall aim is to enhance access control and authentication mechanisms in the home IoT environment by considering user preferences and specific device capabilities.
### Introduction
1. **Transition to IoT in Homes:**
   - Computing is moving from single-user devices to the Internet of Things (IoT) in homes.
   - Traditional security measures are insufficient for the complexities introduced by multiple users interacting with a single device.

2. **Lack of Attention to Access Control and Authentication:**
   - Existing research has primarily focused on insecure software practices, information flows, and challenges in patching IoT devices.
   - Access control and authentication for home IoT devices have been overlooked.

3. **Challenges in Home IoT:**
   - Home IoT devices are shared among multiple users within a household.
   - Lack of screens and keyboards in many IoT devices complicates traditional authentication methods.

4. **Real-world Examples:**
   - Instances like Burger King's TV commercial triggering Google Home and South Park affecting Amazon Echo demonstrate vulnerabilities in current access control and authentication.

5. **Capability-centric Model:**
   - Proposes a capability-centric model for access control, defining capabilities as specific actions that can be performed on a particular device.

6. **Research Questions (RQs):**
   - RQ1: Explores if access-control policies differ among capabilities of single home IoT devices.
   - RQ2: Investigates consistent access-control policies across participants for specific relationships and capabilities.
   - RQ3: Examines contextual factors influencing access-control policies.
   - RQ4: Identifies authentication methods balancing convenience and security.

7. **User Study:**
   - Conducts a 425-participant online study to understand desired access-control policies for 22 home IoT capabilities.
   - Validates the need for policies based on capabilities rather than devices.

8. **Default Policies and Contextual Factors:**
   - Explores default access-control policies based on user relationships and capabilities.
   - Identifies contextual factors, including location, age, and device location, influencing access-control decisions.

9. **Authentication Methods:**
   - Examines authentication methods that balance convenience and security.
   - Considers consequences of falsely allowing or denying access when evaluating authentication mechanisms.

10. **Rethinking Access Control and Authentication:**
    - Aims to initiate a reevaluation of access control and authentication mechanisms tailored for the unique characteristics of home IoT environments.
### Threat Model
1. **Adversaries in Smart Homes:**
   - Two major classes of adversaries in smart homes are external third parties and those with legitimate physical access to the home.
   - External adversaries exploit software vulnerabilities in platforms, devices, or protocols for malicious purposes.
   - Insiders with legitimate access include household members like temporary workers or children.

2. **Focus on Insider Threats:**
   - This paper focuses on insider threats, particularly household members with legitimate access to the smart home.
   - Insider threats may arise due to various motivations, from curiosity to willful disobedience, or attempts to correct imbalances introduced by certain IoT devices.

3. **Less Research on Insider Threats:**
   - Insider threats have received less research attention compared to external threats in smart home security.
   - Motivations for insider threats include curiosity, disobedience, and addressing power imbalances resulting from surveillance implications.

4. **Domestic Setting Assumption:**
   - The paper assumes a domestic setting where occupants control home IoT devices through various means such as smartphones, voice assistants, rules, and physical interaction.
   - Examples include a maintenance worker unlocking the front door via a smartphone app and a child controlling lights through a voice assistant.

5. **Access-Control Rules:**
   - The goal is to establish access-control rules that effectively balance security, privacy, and functionality in the smart home environment.

These points provide an overview of the paper's focus on insider threats in smart homes and the aim to develop access-control rules that consider various factors.
### Affordances of current devices
1. **Affordances of Current Devices:**
   - Current home IoT devices have limited affordances for access control and authentication.
   - Smartphone apps are commonly used to control devices, with various access-control settings.
   - Representative samples include the Nest Thermostat, August Smart Lock, Withings wireless scales, and Apple HomeKit.
   - Access-control models may be binary (full or no access) or slightly richer, allowing time-based rules and distinctions between local and remote control.
   - Some devices offer limited access-control policy specification, such as Samsung SmartThings, which allows restricting third-party apps from accessing certain capabilities.

2. **Need for Richer Vocabulary:**
   - Current mechanisms are considered rudimentary and lack the necessary vocabulary for specifying access-control rules in complex, multi-user environments.
   - The goal is to establish a richer vocabulary for access-control policies.

3. **Authentication Methods:**
   - Current authentication methods for home IoT devices are often adapted from smartphone and desktop paradigms.
   - Passwords are widely used, and smartphone apps often require users to authenticate with a password.
   - Voice-based authentication is rudimentary and currently used more for personalization than security. For example, Google Home uses speaker recognition for customizing reminders but not for security-related tasks.

These points highlight the limitations of current home IoT devices in terms of access control and authentication, emphasizing the need for more sophisticated vocabulary and methods in multi-user environments.
### Studies conducted
1. **Pre-Study on Capabilities and Relationships:**
   - The pre-study aimed to identify capabilities and relationships relevant to access control in the home IoT.
   - Home IoT devices were grouped into categories such as smart-home hubs, door locks, and voice assistants.
   - Capabilities offered by currently marketed devices in each category were collected.
   - Future capabilities and the ability to write end-user programs were also considered.
   - Participants were shown capabilities for a specific device category, and they answered questions about positive and negative consequences, identifying additional expected capabilities.
   - The pre-study identified a comprehensive set of capabilities, ranging from those with substantial concerns to those with none.
   - Relationships were also explored, with participants grouping them into ordered levels of desired access to smart-home devices.

2. **Selection of Capabilities and Relationships:**
   - The study selected 22 capabilities from the pre-study results, representing a spectrum of opinions and concerns while being representative of smart homes.
   - Relationships were narrowed down to six, spanning the full range of desired access and showing consistency in participants' assignments to access categories.

This pre-study process involved gathering insights into user concerns and expectations regarding capabilities and relationships in the context of home IoT devices, laying the groundwork for the main study on access control and authentication.
### Methodology
**Methodology (Continued):**
   - The study aimed to understand access control preferences in the home IoT through an online survey-based user study conducted on Mechanical Turk.
   - **Participant Recruitment:**
      - Participants were recruited from Mechanical Turk, and eligibility criteria included age 18+, U.S. residency, and a minimum approval rating of 95%.
   - **Survey Design:**
      - Participants were presented with a single capability randomly chosen from a pool of 22 identified in a pre-study. Relationships (e.g., spouse, teenage child) were also randomly assigned.
      - The survey included questions about desired access-control policies, authentication methods, and contextual factors influencing access decisions.
   - **Compensation and Duration:**
      - Participants were compensated $3.50 for their involvement, and the study duration was approximately 20 minutes.
   - **Ethical Considerations:**
      - The study received Institutional Review Board (IRB) approval.

#### 4. **Analysis:**
   - **Data Coding:**
      - Responses included both qualitative free-text and multiple-choice data, coded independently by two researchers using an open coding approach.
   - **Quantitative Analysis:**
      - Quantitative analysis involved chi-squared tests and Fisher’s Exact Test (FET) to compare multiple-choice responses across different groups, with adjustments for multiple testing.
   
#### 5. **Limitations:**
   - **Ecological Validity and Generalizability:**
      - The study acknowledged limitations in terms of ecological validity and generalizability due to the use of a convenience sample from Mechanical Turk.
      - Participants had varying levels of prior experience with home IoT devices, introducing potential biases.

#### 6. **Results (Selected Findings):**
   - **Participant Demographics:**
      - A total of 425 participants, with nearly equal gender representation, participated in the study.
      - Participants were primarily aged between 25 and 54, living in diverse household configurations.
   - **Capability Preferences:**
      - Participants exhibited varied attitudes toward different capabilities within a single device, indicating a need for fine-grained access-control mechanisms.
      - Certain capabilities, such as deleting IoT lock activity logs, showed lower permissibility compared to others, suggesting sensitivity to specific actions.
   - **Context-Dependent Access:**
      - The capability of "Answering the Doorbell" was identified as highly context-dependent, with permissions influenced by factors like the homeowner's presence.
      - Contextual factors, including time of day, location, and usage, were explored as influencers of access control decisions.

These detailed key points provide a comprehensive overview of the study's methodology, participant recruitment, survey design, ethical considerations, data analysis approaches, identified limitations, and specific findings related to participant demographics and access control preferences in the home IoT.
#### 6. **Results (Continued):**
   - **Relationships (RQ1):**
      - **Babysitter vs. Visiting Family:**
         - Participants exhibited consistent attitudes toward babysitters and visiting family members, considering them part of a guest-like group.
         - No significant differences were observed between these two relationships, indicating shared trust with the homeowner.
         - Visiting family members generally had slightly more permissive policies, but specific capabilities showed nuanced variations.
         - Certain capabilities, like "Live Video," were more permissively granted to babysitters due to their caregiving role.
         - The importance of both relationship-based and capability-based access control models in a smart home was emphasized.
      - **Child vs. Teenager:**
         - Teenagers (16 years old) and children (8 years old) were given different access scopes, with teenagers generally having greater access.
         - A teenager was often regarded as a young adult, resulting in wider trust and more permissive access settings.
         - Concerns about young children misusing capabilities and potential dangers led to more restrictive access settings for them.
         - Differences in attitudes toward capabilities like "Order Online" showed nuanced variations between teenagers and young children.
      - **Overall Preference for Restrictive Policies:**
         - Participants, except for spouses and teenagers, generally preferred more restrictive access-control policies.
         - For many capabilities, participants chose "never" or "sometimes" more frequently than "always."
         - A small percentage of participants chose "always" for visiting family members (18.1%), babysitters (10.3%), children (8.3%), and neighbors (0.7%).
         - Limited permissiveness was observed for capabilities like controlling lights and music, deemed less likely to cause harm.

These detailed key points elaborate on the findings related to relationships in the context of access control preferences in the home IoT. The discussion includes nuanced variations in attitudes toward babysitters and visiting family members, the differing access scopes for children and teenagers, and the overall preference for more restrictive access-control policies, particularly for certain relationships.
### Conclusions
### Detailed Key Points (Continuation):

#### 7. **Discussion:**
   - **Capabilities, Relationships, and Context:**
      - Current access control models in smart homes are often device-centric, but the study advocates for a capability- and relationship-centric model, aligning more closely with user expectations.
      - The study reveals nuanced variations within a single device based on relationships and contextual factors, emphasizing the need for a more flexible access-control mechanism.
      - The proposed model provides a concrete vocabulary for developers, enhancing the design of future smart-home devices.
   - **Default Policies and Access Control Setup:**
      - Default policies derived from the study suggest simplicity in multi-user social environments, aligning with non-IoT policies.
      - Future smart-home setups could involve guiding users through a questionnaire based on the study's vocabulary to establish access-control policies, minimizing user burden.
   - **Authorization Vocabulary:**
      - The study proposes an authorization vocabulary based on triplets: <Capability, UserType, Context>, where capabilities, user types, and contextual factors are integral components.
      - UserType categories include Spouse, Teenager, Child, Babysitter, and Neighbor, capturing the diverse relationships in a smart home.
      - Contextual factors, such as Time, User Location, Age, People Nearby, Cost of Resource, Device State, Device Location, and Usage History, are identified as crucial components.
   - **Mapping Authorization and Authentication:**
      - The study briefly addresses authentication mechanisms, discussing their implications on user identification, relationships, and contextual factors.
      - Authentication mechanisms, including smartphones, wearables, voice assistants, computer vision, and bilateral/continuous authentication, are evaluated for their suitability and potential privacy concerns.
      - Privacy limitations, false positive/negative tuning, and potential privacy-preserving solutions are considered for each authentication mechanism.
   - **Future Work:**
      - The study acknowledges the need for continued work in translating observations into fully usable prototypes and supporting richer capabilities and interactions in the home IoT.
These detailed key points expand on the discussion section, covering topics such as the proposed authorization vocabulary, implications for access control setup, and the evaluation of authentication mechanisms in the context of smart homes. The study's insights lay the groundwork for future developments in home IoT access control and authentication systems.