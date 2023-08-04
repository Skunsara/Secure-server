# Project Name: WIKI

## Table of Contents
1. [Introduction](#introduction)
2. [Group Members](#group-members)
3. [Roles](#roles)
4. [Challenges](#challenges)
5. [Solutions](#solutions)
6. [Tools Used](#tools-used)
7. [Tests](#tests)
8. [Results](#results)
9. [Possible Improvements](#possible-improvements)
10. [Conclusion](#conclusion)
11. [Acknowledgments](#acknowledgments)

## Introduction
WIKI is a project aimed at creating a secure wiki pentesting website hosted on a virtual machine (VM). The main objective of this project is to build a wiki platform that provides comprehensive information on various penetration testing techniques and tools while ensuring the security of the VM infrastructure.

## Group Members
- Amin (PO and Dev)
- Maikl (SM and Dev)

## Roles
- Amin: Product Owner and Developer. Responsible for defining project requirements, setting up the VM, configuring nftables firewall, implementing SSH hardening, and deploying the wiki pentesting site.
- Maikl: Scrum Master and Developer. In charge of coordinating the development process, setting up fail2ban, conducting security tests using Lynis, and configuring Apache and Wikimedia for the website.

## Challenges
- Setting up the VM and configuring the nftables firewall required understanding the new nftables syntax and adapting to the changes from iptables.
- Implementing SSH hardening was complex as it involved disabling certain SSH features without disrupting functionality.
- Building a comprehensive and secure wiki platform while ensuring ease of content management and user-friendly experience.

## Solutions
- For nftables setup, we studied the documentation and resources available online to learn the new syntax and successfully configured the firewall rules to enhance security.
- SSH hardening was achieved by carefully updating the `sshd_config` file, disabling root login, and using public key authentication.
- We followed best practices and documentation to integrate Apache and Wikimedia, ensuring proper website functionality and security.

## Tools Used
- nftables: A new packet filtering framework used as an alternative to iptables for firewall configuration.
- Lynis: A security auditing tool used to assess the security level of the VM and identify potential vulnerabilities.
- Apache: The web server software utilized to host the wiki pentesting site and serve web pages.
- Wikimedia: The content management system used for creating and managing the wiki's content.

## Tests
- We conducted security tests using Lynis to assess the VM's security posture and identify any potential weaknesses.
- We performed SSH login attempts to trigger fail2ban and verified that IP addresses were correctly banned.
- Extensive testing was carried out on the Apache server and Wikimedia platform to ensure smooth website functionality and security.

## Results
- The nftables firewall effectively protected the VM from unauthorized access and potential threats by filtering incoming and outgoing traffic.
- SSH hardening significantly improved the SSH server's security by restricting access and promoting secure authentication methods.
- Fail2ban successfully blocked IP addresses that exceeded the defined failed login attempts, mitigating the risk of brute-force attacks.
- The wiki pentesting site created using Apache and Wikimedia provided an easy-to-use platform for content management, with improved security measures in place.

## Possible Improvements
- Regularly update and monitor the security of the VM and its components to address any new threats or vulnerabilities.
- Continuously expand and update the wiki content to provide a comprehensive and up-to-date resource for penetration testing enthusiasts.

## Conclusion
The WIKI project successfully created a secure and user-friendly wiki pentesting site hosted on a virtual machine. The collaboration between Amin and Maikl as the Product Owner, Scrum Master, and Developers proved to be effective in achieving our objectives and delivering a valuable resource for the penetration testing community.

## Acknowledgments
We would like to thank the team for their efforts and collaboration throughout this project.
