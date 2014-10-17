##Mangy Beast
===========

###CloudPassage Halo policy for detecting vulnerability to CVE-2014-3566 (AKA POODLE)

**We're not going to rehash the minute details of CVE-2014-3566, otherwise known as POODLE.  If you've found your way here, you're likely looking for a method to reliably detect and remediate.**

**Background:**  POODLE affects the Secure Sockets Layer (SSL) protocol version 3.  The danger is that an attacker who can manipulate network traffic and intercept packets from an SSLv3-encrypted datastream can potentially determine the repeated contents of the datastream (like a session key in a cookie).

**Detection:**  Download the mangy-beast.policy.json file and upload it into your Halo portal account.  Assign the policy to a group containing supported workload images (see supported platforms, below) and force a scan across all suspects.  Bear in mind that there are two configuration item checks that will conflict for workloads running mod_nss.  Earlier versions don't have as broad support of TLS as newer versions, so if you see alerts from the mod_nss set of checks you may need to disable the one that doesn't apply to your workloads.  If you're scanning against multiple OS versions (RHEL5.10 and RHEL6.5, for instance) you should clone this policy and disable the inappropriate rule for each use case.

**Remediation:**  Disable the unsafe protocol versions in your Apache configs.  Specific details can be found in the remediation instructions within the policy.

**Supported platforms:** RHEL-ish operating systems running Apache (tested on CentOS and Oracle Linux versions 5.10 and 6.5)
