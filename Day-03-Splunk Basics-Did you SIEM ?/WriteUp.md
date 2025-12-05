## 📝 Overview
  Today's challenge was Splunk basics and how do we use this in SIEM.
  Splunk in cybersecurity is a powerful data platform used for real-time security monitoring, threat detection, investigation, and response by ingesting, analyzing, and visualizing vast amounts of machine data from across IT environments.
  It acts as a leading Security Information and Event Management (SIEM) solution to spot anomalies, automate workflows (Splunk SOAR), and provide insights for compliance and forensics, helping security teams protect against modern threats. 
  Today's challenge required us to analyze certain logs and then answer the related questions using the Splunk software.

## 🛠 Tools Used
  Splunk Enterprise

## 🚀 Steps I Followed
  Started a basic search across the index using your custom source type web_traffic, using the following query:<br>
  Search query: `index=main sourcetype=web_traffic`<br>
  Then I found whether there has been any abnormal amount of requsts to web server which might indicate of an attack attempt using the query:<br>
  Search query: `index=main sourcetype=web_traffic | timechart span=1d count | sort by count | reverse `<br>
  After finding that there has been a huge amount logs on particular days it was time to narrow doen our search. First I found the requests coming from a not so truted user agent and the suspicious client ip        using:<br>
  Search query: `sourcetype=web_traffic user_agent!=*Mozilla* user_agent!=*Chrome* user_agent!=*Safari* user_agent!=*Firefox* | stats count by client_ip | sort -count | head 5`<br>
  After finding the ip address,it was time to trace the attack attempt chain and search for common path traversal and open redirect vulnerabilities using:<br>
  Search query: `sourcetype=web_traffic client_ip="<REDACTED>" AND path="*..\/..\/*" OR path="*redirect*" | stats count by path`<br>
  After finding that the attacker went beyond normal scanning it was time to check for if any outbound C2 communicatiopn was established between the malicious ip and the compromised server using:<br>
  Search query: `sourcetype=firewall_logs src_ip="10.10.1.5" AND dest_ip="<REDACTED>" AND action="ALLOWED" | table _time, action, protocol, src_ip, dest_ip, dest_port, reason`<br>
  After confirming that there was indeed a connection established, i checked for whether if any data was exfiltrated or not using the query:<br>
  Search Query: `sourcetype=firewall_logs src_ip="10.10.1.5" AND dest_ip="<REDACTED>" AND action="ALLOWED" | stats sum(bytes_transferred) by src_ip`<br>
  The results show a hugh volume of data transferred from the compromised webserver to C2 server.<br>

## ❓ Questions & Answers
  The answers to today's questions could easy be found using the above listed queries with minute tweeks and analyising the results of the queries.

## 🧠 Learnings
 ### Today I learnt :
  The basics of Splunk as a SIEM solution<br>
  Ingesting and interpreting custom log data in Splunk<br>
  Creating and applying custom field extractions<br>
  How to conduct an investigation within Splunk to uncover key insights<br>

