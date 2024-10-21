# Cybersecurity Incident Report

## Report Analysis Description

This report analyzes a recent cybersecurity incident involving a Denial of Service (DoS) attack on the company's web server. The analysis includes a detailed examination of the attack's characteristics, its impact on system availability, and the mechanisms exploited by the attacker. By reviewing network logs captured during the incident, this report highlights key vulnerabilities and provides actionable recommendations for enhancing security measures and preventing future incidents.

## Scenario Review

A security analyst for a travel agency received an automated alert indicating a problem with the company’s web server. Upon attempting to access the website, a connection timeout error occurred. Analysis using a packet sniffer revealed a high volume of TCP SYN requests from an unfamiliar IP address, suggesting a possible attack. 

The web server was overwhelmed, leading to a temporary offline state for recovery. The firewall was configured to block the suspicious IP address, although this measure is only a temporary solution. Immediate communication with management was required to discuss further steps to mitigate the attack and prevent future incidents.

## Wireshark Log Analysis

![image](https://github.com/user-attachments/assets/7fb54c88-9d46-4e4f-839f-035550a5779b)

## Detailed Incident Analysis

### Section 1: Type of Attack

The incident is likely a **Denial of Service (DoS) Attack**, specifically a **SYN Flood Attack**. 

- **Nature of Attack**: The attacker sent numerous TCP SYN requests to the web server (203.0.113.0), overwhelming its resources.
- **Impact on Availability**: This attack resulted in high resource utilization and connection timeouts for legitimate users, violating the principle of availability in the CIA triad.

### Section 2: Attack Mechanism

The attack exploited the TCP three-way handshake:
1. **SYN Request**: The attacker sends multiple SYN packets.
2. **SYN-ACK Response**: The server acknowledges the requests but waits for an ACK that never comes.
3. **Resource Exhaustion**: The server ties up resources for each half-open connection, leading to unresponsiveness for legitimate requests.

### Log Analysis

- **Entries 63-68**: Indicate multiple SYN packets from various IP addresses to the server, overwhelming its capacity.
- **Entries 69-78**: Show a pattern of unanswered SYN requests, tying up server resources and leading to timeouts for legitimate users.

## Incident Summary and Recommendations for Remediation

### Section 3: Summary of The Incident

The SYN flood attack caused the company's web server to become unresponsive, impacting service availability and leading to potential revenue loss and reputational damage.

### Recommendations for Prevention and Remediation
- **Implement Rate Limiting**: Enforce limits on SYN packets to control traffic volume.
- **Enable SYN Cookies**: Utilize SYN cookies to efficiently manage connections.
- **Use Load Balancers**: Distribute incoming traffic across multiple servers to mitigate overload.
- **Monitor Logs**: Regularly review logs for unusual SYN request patterns.
- **Keep Systems Updated**: Ensure all systems receive timely security patches.
- **Consider DDoS Protection Services**: Engage services specifically designed to combat DDoS attacks.
- **Develop an Incident Response Plan**: Create and regularly practice a response strategy for potential attacks.
- **Employee Education**: Train staff to recognize and report suspicious activities.

By implementing these recommendations, the organization can enhance its resilience against future attacks, safeguard its digital assets, and maintain continuous service availability.
