# Security

## Introduction

Security is a critical aspect of any application, and Highrise Studio is no exception. Here are some best practices to keep in mind when writing Lua code for your game:

### 1. Client and Server Communication

When developing multiplayer games, it's essential to distinguish between client-side and server-side code. Client-side code runs on the player's device, while server-side code runs on the game server. It's crucial to validate and sanitize user input on the server to prevent cheating and hacking attempts.

For example, if you were to transfer Gold from the **World Wallet** to the player account, you should perform this operation on the server and not involve the client directly. This way, you can ensure that the transaction is secure and cannot be manipulated by the player.

<Note type="warning">
Firing events from the client to the server should be done with caution. Client events can be intercepted and manipulated by malicious players. Always validate and sanitize input on the server to prevent unauthorized actions.
</Note>

### 2. Regularly Update Your Code

Security vulnerabilities can arise due to outdated libraries, frameworks, or dependencies. It's essential to keep your codebase up to date with the latest security patches and updates. Regularly review your code for potential vulnerabilities and address them promptly.

### 3. Promptly Respond to Security Reports

If a player or security researcher reports a vulnerability in your game, respond promptly and investigate the issue. Take the necessary steps to fix the vulnerability and inform the reporter once the issue has been resolved. Transparency and communication are key when addressing security concerns.

### 4. Implement Secure Coding Practices

Follow secure coding practices to minimize the risk of security vulnerabilities in your Lua scripts. Some best practices include:

- Avoid hardcoding sensitive information like passwords or API keys.
- Use encryption for sensitive data transmission.
- Validate user input to prevent injection attacks.
- Implement access controls to restrict unauthorized actions.

### 5. Log Security Events

Logging security events and suspicious activities can help you identify potential threats and security breaches. Monitor your game logs regularly and investigate any anomalies or unauthorized access attempts. By tracking security events, you can proactively address security issues before they escalate.

## Conclusion

By following these security best practices, you can protect your Lua scripts and ensure a secure gaming experience for your players. Security should be a top priority in your game development process to safeguard player data and maintain the integrity of your game. Stay vigilant, stay informed, and stay secure. 