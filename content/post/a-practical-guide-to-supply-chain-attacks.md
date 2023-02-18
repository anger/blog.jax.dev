---
author: "Jax"
slug: "a-practical-guide-to-supply-chain-attacks"
aliases: ["/a-practical-guide-to-supply-chain-attacks"]
title: "A Practical Guide to Supply Chain Attacks"
summary: "A practical guide to Supply Chain Attacks in a cyber environment. "
tags: ["Attacks", "Hacking"]
date: 2022-12-11T06:59:00Z
draft: false
---
## Introduction  
Our lives revolve around code created by others we do not know. From the QR codes we scan to get the menu at a restaurant to the ad-infested app we download to waste time, all of these applications require huge amounts of code to operate, with most of this code not even being created by the organization using it.

To avoid "reinventing the wheel," organizations must utilize open source software to produce an application in a reasonable timeline without unnecessarily wasting resources.

##### DISCLAIMER  
This blog post in no way argues against open-source software; in fact, it's just the opposite. With greater scrutiny of open source software and its code, we can build a safer, more productive community.

## Defining a Supply Chain Attack  
Wired Magazine's [Andy Greenberg](https://www.wired.com/story/hacker-lexicon-what-is-a-supply-chain-attack/) defined a supply chain attack as "a technique in which an adversary slips malicious code or even a malicious component into a trusted piece of software or hardware." But it can be argued that this definition is too niche, and as such, I think a better definition would be "an attack in which an adversary directly targets the supplier of a good in order to harm a consumer of it." By doing this, threat actors can then use this trusted piece of software to send updates, invoices, and even physical equipment in order to gain privileged access to all the companies that rely on this trusted supplier's product.

## Supply Chain Attack Challenges  
Supply chain attacks often come with different risks and are more challenging to deal with than traditional forms of cyberattacks. Between the difficulty in detecting these attacks and the widened scope, sometimes involving multiple entities, it is not a surprise these attacks are hard to deal with.

### Scope is Widened   
Social engineering and the exploitation of vulnerabilities are scary things, often causing a lot of damage. However, their scope is usually limited to a single entity.

This is different, however, in a supply chain attack, as these occur downwind from a compromised organization. 

### Visibility Issues  
Most software engineers do not fully know what makes up the product they are working on, and most companies do not have the resources to track each individual component of a package. A single library can have dozens of dependencies, and those dependencies can have their own dependencies as well. This leads to a lack of visibility that can lead to supply chain attacks.

## Who's involved?
Threat actors involved in these kinds of attacks can range from seemingly harmless script kiddies to massive, state-sponsored APTs.

### Individuals   
Whether they are looking for a quick buck, or to get revenge, individuals are often perpetrators of supply chain attacks.

These attacks can happen when an individual social engineers their way into a git repo's priority position or when a developer goes rogue and targets their own repo.

### Organized Crime  
Organized groups often look toward the web for a quick payday. Through targeting the supply chain, organized crime can kill multiple birds with one stone.

### State Funded Groups  
Also known as "State Actors" or  
"APT's": these groups are those funded by those in the big leagues: governments and militaries.

These groups often target other countries or the citizens/companies of those countries. This can be done for financial or monetary motives, and a big example of such an attack is the SolarWinds attack, which was believed to have been done by Cozy Bear, a group sponsored by the Russian government.

## Attack Vectors  
Below are common attack vectors in a Supply Chain Attack.   
- Vulnerable Open Source Dependencies   
- Vulnerable Update Servers  
- Vulnerable Hardware Devices/Appliances  
- Insufficient employee training against social engineering

## Prevention  
Below are some ways to mitigate and prevent supply chain attacks from occurring.   
- Strictly enforce multi-factor-authentication  
- As soon as possible, install security updates.  
- Implement integrity controls.  
- Examine all digital signatures.  
- Have a strong Supply Chain Vetting process.   
- Prepare for the inevitable.   
    - Having a good incident response process is vital for all organizations.

## Conclusion  
Hackers utilize supply chain attacks because they work. They’re simple, effective, and cheap, allowing an organization's lack of security awareness to do almost all of the work for them. Thankfully, attention to supply chain attacks after the SolarWinds attack has been growing, and with it, the defenses of companies and organizations have been strengthening. It is wishful thinking to think that supply chain attacks will cease to be effective anytime soon, but with time and awareness, we can hope that the vectors of compromise decrease little by little until eventually supply chain attacks are just another attack vector we can peacefully ignore.