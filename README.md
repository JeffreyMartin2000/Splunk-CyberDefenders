# Splunk-CyberDefenders
What I learned using Splunk on CyberDefenders.com

<img width="540" alt="Screenshot 2023-05-15 195651" src="https://github.com/JeffreyMartin2000/Splunk-CyberDefenders/assets/129632324/b187c62b-7973-4e3b-86da-a0f5187ae8d3">

I will show a couple of examples where we did some investigation and search commands to find the name of the file that defaces the website and the Cerber infection script and the length of the script for practice. 

<img width="506" alt="nameoffilethatdefacedwebsiteSolution" src="https://github.com/JeffreyMartin2000/Splunk-CyberDefenders/assets/129632324/60a2911f-2a60-4cee-bb4e-0d4e57daae60">

So the website is defaced by the "poisonivy" group. The server hosting the website was breached and we need to identify what the IP address is for the imreallynotbatman.com web server. We found that the host web server is "192.168.250.1". The attacker first took control of the web server, then uploades an image to the website page from the web server itself. That means we need to search that IP address as the source IP. Another search string I incorporated was the file type. I inputed .jpg or .jpeg

And after looking through the logs I found this

<img width="748" alt="nameoffilethatdefacedwebsite" src="https://github.com/JeffreyMartin2000/Splunk-CyberDefenders/assets/129632324/cfec4221-bd76-4a11-a099-bb76c958d9a1">

Now lets find that script to understand what the attacker is doing here

<img width="525" alt="VBscriptLengthsolution" src="https://github.com/JeffreyMartin2000/Splunk-CyberDefenders/assets/129632324/148ea045-7279-4d60-bc6d-aa283cf0bfc7">

Same as the previous activity I will be identifying what file extention the script has. We are informed that this is a VBscript. So the file extention will be .vbs

We will then use 'eval' to modify the 'length' of the command line input of the script. By using the 'table' command, we specify the fields such as the 'time', 'cmdline', and 'length'. The length is 4490.

<img width="956" alt="VBscriptsearchcmd" src="https://github.com/JeffreyMartin2000/Splunk-CyberDefenders/assets/129632324/cf875e82-8b16-443e-9f53-516a828550fb">

Boss Of the SOC v1 on CyberDefenders.com has made me better at using Splunk. I also learned about how to navigate logs and what commands can help us find any malicious activity. In this writeup I learned how to find a file that defaced a website, and what script is initially used by attackers that implemented ransomware.
