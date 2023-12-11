### Abstract
- Authors look into how private information can be leaked from network traffic generated in the smart home network.
- Several research techniques were proposed to infer IOT device types or user behaviors under clean and ideal environmental setup, but the effectiveness of such approaches become questionable in the complex but realistic network environment, where common techniques like Network Address and Port Translation (NAPT) and Virtual Private Network (VPN) are enabled.
- The main outcomes of this paper are 
	- 1. **Proposed Traffic Analysis Framework:**
	   - The authors introduce a traffic analysis framework that relies on sequence-learning techniques, specifically Long Short-Term Memory (LSTM). This framework leverages temporal relations between packets for the purpose of attacking device identification.
	
	2. **Evaluation Under Varied Environments:**
	   - The framework underwent evaluation in different environment settings, including pure-IoT and a noisy environment with multiple non-IoT devices. Despite these diverse conditions, the results demonstrated the framework's ability to differentiate device types with high accuracy.
	
	3. **Implications for IoT Privacy:**
	   - The findings suggest that IoT network communications present significant challenges to users' privacy, even when protected by encryption and altered by the network gateway. This underscores the need for the development of new privacy protection methods specifically tailored to mitigate the identified privacy issue in IoT traffic.
### Introduction
- **Key Points:**

1. **IoT Growth and Smart Home Privacy Concerns:**
   - The Internet of Things (IoT) is rapidly expanding across various sectors, with the global market projected to grow significantly. The Smart Home, a prominent IoT application, introduces potential privacy threats as attackers could intercept network packets to infer private information about residents and their IoT devices.

2. **Privacy Assessment of Smart Home Residents:**
   - The paper aims to assess the privacy threat to Smart Home residents by evaluating different traffic-analysis approaches on datasets containing real IoT traffic. It highlights that existing works often assume local adversaries or simplified network environments, leaving the effectiveness of traffic analysis under remote adversaries or complex networks unexplored.

3. **Traffic-Analysis System - HomeMole:**
   - The authors present a traffic-analysis system called HomeMole designed to automatically infer IoT devices in a Smart Home network, even when facing challenges like Network Address and Port Translation (NAPT) and Virtual Private Network (VPN). Two LSTM models, including a bidirectional LSTM model, are introduced for identifying IoT devices based on analyzed packets.

4. **Evaluation Results and Model Performance:**
   - The study evaluates the system under different network configurations (NAPT and VPN) and scenarios (pure-IoT and noisy environment). Results show that the proposed models, particularly the bidirectional LSTM model, outperform the baseline model (Random Forest) in accuracy. The bidirectional LSTM model achieves high accuracy even in the presence of non-IoT traffic, showcasing its effectiveness in modeling temporal relations between packets.

5. **Contributions and Open Resources:**
   - The contributions of the work include the development of the HomeMole system, the evaluation of models under various network conditions, and the release of datasets and models on GitHub. The release aims to facilitate further research in traffic analysis methods and assist the IoT community in enhancing security defenses.
### Background
1. Related Work
	1. Network Traffic Analysis
		1. **Effectiveness of Network Traffic Analysis:**
		   - Network traffic analysis has demonstrated effectiveness in various applications, including anomaly detection, software identification, and device fingerprints.
		
		2. **Wireless Device Fingerprinting:**
		   - Sakthi et al. applied statistical techniques to create unique fingerprints for multiple wireless devices by analyzing network traffic. Even in the presence of interference from other wireless users, the approach achieved satisfying accuracy.
		
		3. **Wearable Fingerprinting with Bluetooth Traffic:**
		   - Aksu et al. introduced a wearable fingerprinting framework based on Bluetooth traffic. Their evaluation demonstrated that wearable devices could be accurately fingerprinted using Bluetooth classic protocols.
		
		4. **App Identification Framework:**
		   - Taylor et al. proposed an identification framework, AppScanner, for smartphone apps. AppScanner extracts statistical features from network flows and, when trained with different learning algorithms, achieved the highest accuracy of 99.8% on 110 apps.
		
		5. **Online Traffic Classification Framework:**
		   - Chen et al. proposed an online traffic classification framework utilizing kernel methods and deep neural networks. Their approach, evaluated on 5 different protocols and 5 mobile applications, achieved high accuracy rates of 99.84% and 88.43%, respectively.
		
		These examples highlight the versatility and applicability of network traffic analysis in diverse contexts, showcasing its potential in accurately identifying anomalies, software, devices, and applications.
	2. Traffic analysis in IoT domain
		
		1. **IoT Traffic Analysis Trends:**
		   - With the rapid development of the Internet of Things (IoT) ecosystem, characterizing and fingerprinting IoT devices has become a significant and trending topic in recent years.
		
		2. **Distinctive Features in IoT Traffic:**
		   - Apthorpe et al. conducted case studies on four IoT devices, finding distinctive features in network traffic that enable device identification and behavior inference.
		
		3. **IoT Sentinel Device Identification System:**
		   - Marcus et al. proposed the IoT Sentinel, an IoT device identification system. They extracted 23 features from raw packets, including IP options, addresses, ports, and network protocols. However, some features were limited in applicability due to adversary capabilities and complex network configurations like NAPT and VPN.
		
		4. **Network Traces and Traffic Patterns:**
		   - Sivanathan et al. collected network traces of over 20 IoT devices in a campus environment, characterizing device profiles based on traffic patterns. Feature engineering was used, but some features became ineffective in complex network settings, such as NAPT and VPN.
		
		5. **Multi-Stage Privacy Attack in Smart Homes:**
		   - Abbas et al. proposed a multi-stage privacy attack in smart home environments, using machine-learning approaches to reveal different types of privacy information. However, their scenario involved a physical proximity attack, unlike the model in this work that assumes an attacker acquiring network traffic between the gateway and remote server.
		
		6. **Differences in Adversarial Scenarios:**
		   - The research by Abbas et al. differs from the current work in terms of the adversary's location and capabilities. Their attacker is physically within wireless range, while the current model assumes the attacker can acquire network traffic remotely. These differences in adversary capabilities lead to distinct solutions based on the raw network traffic obtained.
		
		These studies collectively contribute to the growing field of IoT traffic analysis, showcasing diverse approaches and considerations for device identification and privacy in various scenarios and network configurations.
	3. Privacy Leakage in IOT apps
		1. **Privacy Leakage in Smart Home Apps:**
		   - The issue of privacy leakage in smart home apps has become a concern in the security community, prompting attention and research in recent years.
		
		2. **Taint Analysis for Sensitive Information Tracking:**
		   - Celik et al. employed taint analysis to track sensitive information in IoT apps. Their evaluation demonstrated that the approach could accurately mark the flow of sensitive data with high accuracy.
		
		3. **NLP-Based Dynamic Analysis for Privacy Risks:**
		   - Babun et al. proposed a dynamic analysis tool based on Natural Language Processing (NLP) to inform users of potential privacy risks when using an IoT app. The evaluation indicated that the tool achieved an average accuracy of 94.25% with minimal execution overhead.
		
		4. **Privacy Leakage Risk in IoT Automation Framework:**
		   - Surbatovich et al. analyzed the risk of privacy leakage in the if-this-then-that (IFTTT) IoT automation framework. Using an information flow model, they found that approximately 50% of the unique IFTTT recipes violated confidentiality or integrity.
		
		5. **Focus on Privacy Leakage in IoT Network Traffic:**
		   - In contrast to previous works, the current focus is on uncovering privacy leakage issues specifically in IoT network traffic. This distinction highlights a unique approach to addressing privacy concerns in the context of IoT applications.
		
		These studies collectively contribute to the understanding of privacy issues in IoT apps, offering different perspectives and tools for identifying and mitigating privacy leakage risks in various aspects of IoT systems.
	
2. Smart Home Network
	1. ![[Pasted image 20231211113244.png]]
	2. **Smart Home Network Parties:**
	   - The smart home network involves four parties: IoT device, service provider, gateway, and user.
	
	2. **Communication Overview:**
	   - The communication schema includes interactions between IoT devices, service providers, gateways, and users.
	
	3. **Types of IoT Devices:**
	   - Two main types of IoT devices are highlighted:
	     - **Sensing Devices:** These devices detect the surrounding environment and send notifications periodically or immediately on an event, such as the Samsung ST Motion Sensor.
	     - **IoT Hub:** Acts as the "brain" or centroid controller for other IoT devices or kits in close range, especially useful for controlling devices using low-power protocols like BLE.
	
	4. **IoT Device Interaction with Service Provider:**
	   - IoT devices interact with a service provider through internet communications. The service provider handles requests, relays resources, and may leverage cloud analytics, such as AWS IoT Core, to process a massive amount of IoT data.
	
	5. **Gateway Role:**
	   - A gateway acts as a bridge between in-home IoT devices and the remote service provider. It typically provides WLAN and LAN interfaces for in-home devices and communicates with the service provider through a WAN interface.
	
	6. **User Control:**
	   - The user takes control of all smart devices in the home through mobile applications or human interactions (e.g., walking, talking, touching).
	
	7. **Device Identifier:**
	   - IoT devices within the smart home network are distinguished by device identifiers determined by specific network protocols. Wi-Fi devices have unique source IP addresses and MAC addresses. IoT kits, even if not using Wi-Fi, obtain identifiers from the IoT hub through other protocols (e.g., NwkAddr for Zigbee devices and Resolvable Private Address for BLE devices).
	   - 
3. Insights into IoT Traffic
	1. ![[Pasted image 20231211113309.png]]
	2. **Similar Traffic Patterns in Device Categories:**
	   - Devices belonging to the same category exhibit similar traffic patterns. For instance, Amazon Echo Dot and Google Voice Assistant, both voice assistants, show comparable traffic bursts and continuous communication with the remote server when activated (refer to Figure 16 and Figure 17 in the Appendix).
	
	2. **Variability in Traffic Patterns Based on Device States:**
	   - Devices in different running statuses can have significantly different traffic patterns. For example, the Orvibo switch produces denser but smaller amounts of traffic in standby mode compared to running mode. Similarly, the Xiaomi camera generates much more traffic in WAN shooting mode than in LAN shooting mode (refer to Figure 18 and Figure 19 in the Appendix).
	
	3. **Diverse Protocol Choices:**
	   - The choice of communication protocols is diverse among IoT devices. Table 1 in the report illustrates the varied protocol choices in terms of packet ratios under different network protocols. Notably, most traffic captured by an attacker is IPv4-based, UDP is commonly adopted by devices with large volumes of traffic (e.g., network cameras), and IoT devices generate less HTTP traffic compared to non-IoT devices.
	
	4. **Protocol Diversity and Device Identification:**
	   - Communication between devices and remote services follows certain conventions reflected in the choice of protocols. While DNS is traditionally used for device identification, the analysis shows that its ratio is relatively low compared to other protocols. Simply relying on DNS may not guarantee accurate device identification, especially when observing traffic from an incomplete session.
	
	These insights emphasize the importance of considering device categories, states, and protocol diversity when analyzing the network communication patterns of IoT devices in real-world scenarios.
4. NAPT & VPN
	1. ![[Pasted image 20231211113335.png]]
	2. **Impact of NAPT and VPN on Network Traffic:**
	3. **NAPT (Network Address and Port Translation):**
	   - **Objective:** To conserve limited global IPv4 resources by enabling the sharing of one IP address among different devices.
	   - **Modification of Identifiers:** NAPT modifies network-layer and transport-layer identifiers, such as destination IP address and destination port numbers, for inbound packets. For outbound packets, it translates the source IP address and source port. The IP address of a local device is replaced with the gateway's IP address.
	   - **Translation Table:** The gateway using NAPT maintains a translation table to record the mapping of addresses and ports, ensuring packets are routed to the correct destination.
	
	2. **VPN (Virtual Private Network):**
	   - **Purpose:** Often used to interconnect different networks, creating a new network with a larger capacity.
	   - **IP Tunneling Mechanism:** Based on the IP tunneling mechanism, hosts in different subnets can communicate securely with authentication and encryption.
	   - **Network Structure:** A VPN-enabled gateway has three network interfaces – wlan0, eth0, and tun0. Wlan0 serves as the entrance of LAN, eth0 establishes the connection between the gateway and WAN, and tun0 is created by the VPN client process.
	   - **Packet Handling:** For every packet from wlan0 to eth0, the VPN client encrypts the original packet into a payload and constructs a new packet. This new packet is delivered to a VPN server, decrypted, and then forwarded to the original destinations.
	   - **Metadata Protection:** From the viewpoint of the destination remote server, the original metadata, such as the source IP address and source port, are completely hidden. This enhances user privacy protection against on-path eavesdroppers.
	
	**Conclusion:**
	   - Both NAPT and VPN introduce modifications to network traffic, impacting the visibility of original device identifiers. These mechanisms play a crucial role in conserving IP resources and ensuring secure communication, but they pose challenges for traffic analysis, especially in the context of preserving user privacy.
5. LSTM-RNN 
	1. ![[Pasted image 20231211113552.png]]
	2. **Key Points on Deep Neural Networks (DNN) and LSTM-RNN:**
		1. **Role of Deep Neural Networks (DNN) in Security:**
		   - DNN has gained traction in the security domain due to its promising results, particularly in feature representation learning.
		   - Example: Rimmer et al. demonstrated the automatic fingerprinting of websites visited by Tor users using DNN.
		
		2. **Recurrent Neural Network (RNN) for Temporal Sequences:**
		   - RNN, a type of DNN, excels in handling temporal-related sequences where historical information is crucial.
		   - Multiple recurrent cells in RNN allow the output of a previous cell to be passed to the current one, preserving and forwarding historical information.
		
		3. **Long Short-Term Memory (LSTM) as a Popular RNN Implementation:**
		   - LSTM-RNN has become a popular choice due to its ability to address weaknesses in other RNNs, such as exploding and vanishing gradients.
		   - **LSTM Memory Cell Components:**
		      - Input gate
		      - Forget gate
		      - Output gate
		   - These gates process data transferred from the previous memory cell and manipulate the current cell state.
		
		4. **Successes of LSTM-RNN in Various Domains:**
		   - LSTM-RNN has achieved success in diverse areas, including speech recognition, medical diagnosis, and system log analysis.
		
		5. **Applicability of LSTM-RNN to IoT Traffic Analysis:**
		   - Inspired by recent research, the problem of IoT traffic analysis is deemed a natural fit for LSTM-RNN models.
		   - Similarities with System Logs: Traffic generated by IoT devices can be organized chronologically, similar to system logs. The contextual dependency between packets, based on the device's running states, can be effectively modeled using LSTM-RNN.
		
		6. **Structure of a Basic LSTM-RNN:**
		   - Figure 3 illustrates the structure of a basic LSTM-RNN, showcasing the input, output, and memory cells.
		
		7. **Problem-Specific Application:**
		   - The nature of IoT traffic, with chronological order and contextual dependencies, aligns well with the capabilities of LSTM-RNN models.
		
		In Section 3, the report is expected to provide detailed insights into how LSTM-RNN models are specifically employed to address the challenges and analyze IoT traffic.
6. Adversary Model
	1. **Objective and Challenges:**
		**Objective:**
		- The primary goal of the adversary is to identify active IoT devices within a targeted smart home.
		
		**Rationale:**
		- Identifying device types in a smart home, as shown by previous work, not only leaks sensitive information about user preferences for IoT products but also serves as a foundation for further inference, such as user behavior detection.
		
		**Privacy Implications:**
		- Privacy leakage resulting from device identification can have negative impacts on users' daily lives. Examples include ISPs inferring device information and selling it to advertisers for targeted advertising, or potential thefts determining when a user is not at home by analyzing outbound traffic and inferring the status of installed surveillance cameras.
		
		**Adversarial Scenario:**
		- The study considers passive eavesdroppers capable of observing encrypted network traffic flowing between the gateway and the remote service.
		
		**Realistic Settings:**
		1. **NAPTs or VPNs Enabled:**
		   - NAPTs or VPNs are enabled in the gateway, resulting in the replacement of original device identifiers by the gateway's. Traffic belonging to different devices is merged, and the contacted remote server becomes opaque to the adversary.
		
		2. **Simultaneous Operation of Multiple Devices:**
		   - Multiple devices, including both IoT and non-IoT devices (e.g., mobile phones, tablets), may operate simultaneously, leading to interleaving packets. Non-IoT devices typically generate packets at a higher rate and in larger volumes than IoT devices, distorting the original statistical features learned on IoT devices.
		
		**Challenges:**
		1. **Traffic Encryption:**
		   - The encrypted nature of network traffic poses a challenge for the adversary in identifying active IoT devices.
		
		2. **Replacement of Device Identifiers:**
		   - The replacement of original device identifiers by the gateway's identifiers, coupled with merged traffic, complicates the task of device identification.
		
		3. **Interleaving of Packets:**
		   - The simultaneous operation of multiple devices, with packets interleaving, introduces complexity and distorts statistical features, making traffic analysis more challenging.
		
		4. **Realistic Remote Adversary:**
		   - Unlike previous works that assumed local adversaries or no traffic fusion, the remote adversary in this study is more realistic. Traffic analysis under these conditions is significantly more challenging.
		
		**Conclusion:**
		- The study addresses the complexities of traffic analysis in a realistic setting, considering encryption, identifier replacement, interleaving packets, and the presence of a remote adversary, aiming to enhance the understanding of IoT device identification in challenging scenarios.
### System Design

**HomeMole: Identifying Active IoT Devices in Smart Homes**

**Goal:**
- The primary objective of HomeMole is to identify active IoT devices within a smart home environment based on their network traffic.

**Three Key Steps:**

1. **Traffic Collection:**
   - **Environment Setup:** HomeMole first sets up the smart home environment.
   - **Raw Traffic Collection:** It collects raw traffic generated by both IoT devices and non-IoT devices under various settings.

2. **Traffic Pre-processing:**
   - **Conversion:** HomeMole pre-processes the collected traffic, converting it into a format recognized by its identification module.
   - **Online Mode Capability:** Unlike fingerprinting at the flow level, HomeMole works at the packet level, assigning a label to each packet after processing. This enables HomeMole to operate in online mode, providing prompt results regarding the current device status.

3. **Traffic Identification:**
   - **Model Training:** The identification module uses the pre-processed data to train models.
   - **Device Identification Task:** These trained models are then used to perform the device identification task.

**Distinguishing Feature:**
- HomeMole operates at the packet level, offering a label for each processed packet, in contrast to methods that perform fingerprinting at the flow level (e.g., [17, 41]).
  
**Advantages:**
- **Online Mode Capability:** HomeMole's packet-level identification allows it to work in online mode, offering real-time results regarding the current device status.
  
- **Versatility in Granularity:** Packet-level identification can be easily adapted to tasks with various granularities, providing flexibility in application (as discussed in Section 5).

**Conclusion:**
- HomeMole's approach distinguishes itself by working at the packet level, allowing for real-time analysis and versatility in handling tasks with different granularities.
### Conclusion & Important Findings
**Analysis of HomeMole's Performance:**

**Challenges with Scarce Traffic:**
1. **Overwhelmed Packets:**
   - IoT devices with low traffic volumes, such as orvibo plug and tplink plug, face challenges as their packets may be overwhelmed by other devices in the same traffic window.
   - Similar frame lengths among different devices can lead to confusion in classification models.

2. **Confusion in Classification:**
   - For example, orvibo plug's three-TCP-packet sequence may be interrupted by packets from other devices, causing incorrect classification, especially in VPN configurations when protocol information is missing.

3. **Impact on LSTM-RNN Models:**
   - LSTM-RNN models perform less effectively in identifying IoT devices with small traffic volumes, particularly in VPN environments where protocol information is often absent.

**Effectiveness of Bidirectional LSTM:**
- Bidirectional LSTM models outperform basic LSTM models, especially in cases where responses from the server differ among devices. Utilizing information from future packets enhances the accuracy of classifying preceding packets.

**Packet-Level Identification:**
- HomeMole's distinctive approach involves classifying all packets within a time period, offering real-time insights into the running status of IoT devices.

**Advantages of Packet-Level Identification:**
1. **Real-Time Running Status:**
   - Allows the adversary to learn the real-time running status of an IoT device based on identified packets.

2. **Versatility in Labeling:**
   - Results of packet-level identification can be used to label objects of any granularity, such as traffic windows or network flows.

**Privacy Threats and Safety Concerns:**
- Privacy threats arise when an adversary can promptly infer device status, potentially compromising user privacy and safety.
- For example, knowing when a network camera is transmitting data continuously can help a thief determine the homeowner's presence and choose the optimal time for a break-in.

**Evaluation of Traffic Window Classification:**
- HomeMole's accuracy in classifying traffic windows, using data from Dataset-Noise in a VPN environment, results in a 0.12 Hamming Loss, indicating that 88% of the labels are correctly matched.

**Defense Against Traffic Fingerprinting Attack:**
- Fingerprinting attacks based on network traffic introduce significant privacy threats, especially when traffic from different devices can be separated.
- Under NAPT and VPN scenarios, accurately pinpointing IoT networks becomes more challenging, leading to accuracy drops ranging from 8.2% to 87.4% in VPN scenarios.
- The need for a principled approach to achieve sufficient protection under all network configurations and device combinations is highlighted.

**Future Exploration:**
- The exploration of local differential privacy (LDP), incorporating noise based on randomized response, is planned to obfuscate IoT traffic and enhance privacy protection.
**Limitations:**

1. **VPN Connections:**
   - The experiment only considered establishing VPN connections using UDP protocols. The option of using TCP (TLS) was not tested. The decision to focus on UDP was based on its widespread adoption and low latency compared to TCP. Future work may explore TCP-based VPN connections and modifications to the packet labeling algorithm.

2. **Behavior Identification:**
   - The evaluation concentrated on device identification, omitting behavior identification. The labeling cost for behavior identification, given large datasets with millions of IoT packets, was a limiting factor. Future exploration may involve efficient approaches to generate labeled behavioral datasets.

**Conclusion:**

In this paper, a systematic evaluation was conducted to assess the effectiveness of traffic analysis in a smart home environment, even in scenarios involving traffic fusion like NAPT and VPN, with both non-IoT and IoT devices active. Leveraging the dependency between packets through DNN models, particularly LSTM-RNN, demonstrated high accuracy in device identification, even in complex network environments.

The results underscore the serious privacy implications of IoT device network communications, even when encryption and traffic fusion are employed. The findings advocate for further research to deepen the understanding of privacy issues in smart home networks and develop mitigation strategies. To support ongoing research in this domain, the release of data and models is made available.