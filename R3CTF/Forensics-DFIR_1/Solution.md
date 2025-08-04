The first three questions were very basic, they asked what is the IP of the attacker and what Vulnerability was used used by the attacker to gain RCE in Subconverter.

**The Answers for the first three were:** 
1. 23.05.4
2. 156.238.233.47
3. CVE-2022-28927

The next question was to find which config file had subconverter call and is causing persistence. This took around a hour to figure out and the answer was **dropbear**.

The next question asked us to find the company name or domain over which th attack was performed. This was quite simple and the asnwer is **portal.r3.internal**.

The last question asked to find the website from which the attacker was hosting the attack from. This took a really long time. Bascially, There was a bootstrap.min.js which actually had the host used by the attacker but it was obfuscated :
I found the malicious js file with a different modification time than the modification time of the files in the same folder, I checked and found that it was an obfuscate js file, after searching I found this decrypt version v7 repo: https://github.com/Mikephie/Decodejs
you install nodejs version 18 and run decrypt,
the output.js file will give the result

(function () {})();
window.location.host == "portal.r3.internal" && (window.location.href = "https://nimble-bonbon-d941a8.netlify.app/");

So, the Solutions for the 6 questions to get the flag were:

1. 23.05.4
2. 156.238.233.47
3. CVE-2022-28927
4. dropbear
5. portal.r3.internal
6. https://nimble-bonbon-d941a8.netlify.app/

This was a very fun forensic question to solve !!!!!
