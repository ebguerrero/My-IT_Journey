# Offensive Security Intro (TryHackMe)

## What is Offensive Security?
- "To outsmart a hacker, you need to think like one."
- Involves breaking into systems, exploiting bugs, and finding loopholes.
- Goal: understand hacker tactics and strengthen defenses.

## Hands-On Lab: Hacking FakeBank
- Launched a TryHackMe virtual machine with the FakeBank website.
- Tool used: **Gobuster** to brute-force hidden directories/pages.
- Command: gobuster -u http://fakebank.thm -w wordlist.txt dir

- Discovered hidden '/bank-transfer' page.
- Performed simulated money transfer to show how vulnerabilities can be exploited.
- Key takeaway: Ethical hackers use these techniques legally to help fix weaknesses.
