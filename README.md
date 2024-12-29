CyS Report - Team 67
Summary
Thepurpose of this penetration testing exercise was to identify vulnerabilities ina web application and simulate
potential exploitation scenarios. The testing revealed multiple vulnerabilities, including hidden pages, exposed
administrative sections, an insecurely stored admin password, anda cross-site scripting (XSS) flaw. These
findings demonstrate significant risks to the application's security posture, which need immediate remediation to
prevent exploitation by malicious actors.
Scope & Methods
Scope
The testing focused on identifying and exploiting vulnerabilities in the web application to evaluate its security
defenses. Specific areas of focus included:
• Hidden orexposed files and directories.
• Administrative sections.
• Input sanitization and handling.
Methods
The following tools and techniques were employed during the testing:
1. Firefox Developer Tools: Used toinspect the application's client-side code and identify hidden files and
paths.
2. Kali Linux: Utilized for running security tools and scripts to further investigate vulnerabilities.
3. NPM (Node Package Manager): Leveraged fordependency and library analysis.
Vulnerability Findings
1. Hidden Scoreboard Page
Description: A hidden "score-board" page was discovered by analyzing the JavaScript file( main. js) using
Firefox Developer Tools. The file contained references to various paths, including one for score-
board. Impact: An attacker could access sensitive information or functionality intended to be
hidden. Recommendation: Implement server-side restrictions and ensure paths are not exposed inclient-side
code.
2. Exposed Admin Section
Description: Similar to the hidden scoreboard page, the admin section path was exposed in
the main. js file. Impact: Unauthorized users could potentially gain access to administrative
functionalities. Recommendation: Obfuscate or eliminate unnecessary path references in client-side code and
enforce strict access controls.
3. Admin Password Exposure
Description: The admin password was exposed through the developer tools, indicating poor handling of
sensitive information in client-side code. Impact: An attacker could gain full administrative access to the
application. Recommendation: Never store or expose sensitive information like passwords in client-side code.
Use environment variables or secure server-side storage.
4. Cross-Site Scripting (XSS)
Description: A reflected XSS vulnerability was discovered in the search functionality. By enteringa crafted
payload such as ‹iframe src=”javascript: alert(document. cookie) "›‹/ifrace›, theattacker was able to
execute malicious JavaScript and access session cookies. Impact: Exploiting this vulnerability could lead to
session hijacking or stealing sensitive user data. Recommendation: Implement input validation and sanitization
on the server side. Use Content Security Policy (CSP) headers to mitigate script execution.
Exploitation and Attack Simulation
1. Hidden Scoreboard Page: By directly navigating to the exposed score- board path, sensitive information
was accessed without authentication.
2. Admin Section: Similar to the scoreboard page, navigating to the admin path provided access to
administrative functionalities.
3. Admin Password: The exposed password allowed full control of the admin account, simulatinga complete
takeover of the application.
4. XSS Attack: Injected JavaScript in the search bar executed successfully, demonstrating the risk of session
hijacking and unauthorized data access.
Conclusion
The penetration testing exercise revealed critical vulnerabilities that pose significant risks to the security of the
web application. Immediate actions are recommended toaddress these issues, including:
• Restricting access to sensitive paths using authentication and authorization mechanisms.
• Removing sensitive information from client-side code.
• Validating and sanitizing all user inputs.
• Implementing security headers to prevent XSS Attacks
