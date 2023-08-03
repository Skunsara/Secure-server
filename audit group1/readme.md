# Project Name: SecureVM

## Introduction
SecureVM is a project aimed at enhancing the security of our virtual machine (VM) by implementing various security measures, including firewall configuration using nftables, SSH hardening, and fail2ban setup. The goal is to protect the VM from potential threats and unauthorized access.

## Group Members
- Amin (PO and Dev)
- Maikl (SM and Dev)

## Roles
- Amin: Product Owner and Developer. Responsible for defining project requirements, setting up the VM, configuring nftables firewall, implementing SSH hardening, and deploying the web server.
- Maikl: Scrum Master and Developer. In charge of coordinating the development process, setting up fail2ban, conducting security tests using Lynis, and configuring Apache and Wikimedia for the website.

## Challenges
- Setting up the VM and configuring the nftables firewall required understanding the new nftables syntax and adapting to the changes from iptables.
- Implementing SSH hardening was complex as it involved disabling certain SSH features without disrupting functionality.
- Configuring Apache and Wikimedia to work together seamlessly and securely required careful consideration of server configurations.

## Solutions
- For nftables setup, we studied the documentation and resources available online to learn the new syntax and successfully configured the firewall rules to enhance security.
- SSH hardening was achieved by carefully updating the `sshd_config` file, disabling root login, and using public key authentication.
- We followed best practices and documentation to integrate Apache and Wikimedia, ensuring proper website functionality and security.

## Tools Used
- nftables: A new packet filtering framework used as an alternative to iptables for firewall configuration.
- Lynis: A security auditing tool used to assess the security level of the VM and identify potential vulnerabilities.
- Apache: The web server software utilized to host the website and serve web pages.
- Wikimedia: The content management system used for creating and managing the website's content.

## Tests
- We conducted security tests using Lynis to assess the VM's security posture and identify any potential weaknesses.
- We performed SSH login attempts to trigger fail2ban and verified that IP addresses were correctly banned.
- Extensive testing was carried out on the Apache server and Wikimedia platform to ensure smooth website functionality and security.

## Results
- The nftables firewall effectively protected the VM from unauthorized access and potential threats by filtering incoming and outgoing traffic.
- SSH hardening significantly improved the SSH server's security by restricting access and promoting secure authentication methods.
- Fail2ban successfully blocked IP addresses that exceeded the defined failed login attempts, mitigating the risk of brute-force attacks.
- The website created using Apache and Wikimedia provided an easy-to-use platform for content management, with improved security measures in place.

## Possible Improvements
- Regularly update and monitor the security of the VM and its components to address any new threats or vulnerabilities.
- Explore additional security tools and technologies to further enhance the VM's overall security posture.

## Conclusion
SecureVM project successfully improved the security of our virtual machine by implementing essential security measures using nftables, SSH hardening, and fail2ban. The collaboration between Amin and Maikl as the Product Owner, Scrum Master, and Developers proved to be effective in achieving our objectives and delivering a secure website.

## Acknowledgments
We would like to thank the team for their efforts and collaboration throughout this project.
