---
layout: post
title: Why .zip domains are a disaster
excerpt: "The infosec community has been buzzing with concern over a recent development that emerged this month: the introduction of .zip domains. The news broke on May 3rd, 2023, when a set of eight domains were released into the wild. Among them were seemingly innocent extensions like .dad, .phd, .prof, .esq, .foo, .zip, .mov, and .nexus. However, hidden within these extensions lies a lurking danger that has captured the attention of security researchers worldwide."
categories: [Guides, Learn]
tags: []
---
## Introduction
The infosec community has been buzzing with concern over a recent development that emerged this month: the introduction of .zip domains. The news broke on May 3rd, 2023, when a set of eight domains were [released](https://twitter.com/Google/status/1653866291692728320) into the wild. Among them were seemingly innocent extensions like .dad, .phd, .prof, .esq, .foo, .zip, .mov, and .nexus. However, hidden within these extensions lies a lurking danger that has captured the attention of security researchers worldwide.

## The Deceptive Nature of .zip Domains
A .zip domain refers to a top-level domain (TLD) that uses the ".zip" extension. While the idea of using a familiar file compression format as a domain extension may seem innovative or even great for hobbyists, it unfortunately introduces substantial security concerns, primarily due to the potential for confusion and deception.

### Domain Spoofing and Phishing Attacks
Threat actors can exploit the familiarity of .zip files and create malicious websites with .zip domains that appear legitimate. These spoofed domains can be used for phishing attacks, where unsuspecting users are tricked into believing they are accessing a trusted website or downloading a harmless file. By clicking on a link from a .zip domain, users may unknowingly expose their sensitive information or install malware on their systems.

### Example
Can you see the difference between these two domains:
![](https://i.imgur.com/IfsfuqE.png)

It just so happens that the second is a redirect to the domain `v2.18.1.zip`. Can you see the potential now?
#### Why it works

It is important to be aware of the potential risks associated with certain URL configurations and how they can be exploited for phishing attacks. In the example provided, there is a difference between the two domains that may not be immediately noticeable to most people. The second domain is actually a redirect to the domain `v2.18.1.zip`, which can be used in malicious ways.

Modern browsers like Chrome, Safari, and Edge have implemented security measures to prioritize user safety. These browsers disregard the user info section of a URL, which includes everything between the scheme (https://) and the @ operator. They focus solely on the hostname portion of the URL.

While this behavior enhances user security by preventing accidental authentication, it can also make certain phishing attacks more believable. Attackers may take advantage of combinations of the @ operator and unicode characters (such as ∕, U+2215) to create deceptive URLs. As the U+2215 slashes are treated as part of the User Info portion of the url, we will be redirected to the malicious site.

For another example, the URL [](https://google.com@jax.dev), will actually take the user to jax.dev. 

It is crucial for users to remain vigilant and exercise caution when interacting with unfamiliar URLs or suspicious websites.
### Difficulty in Identifying Legitimate Sources
The proliferation of .zip domains can make it challenging for users to discern between legitimate and malicious sources. With traditional domain extensions like .com or .org, users have come to associate certain expectations and trust certain websites based on their familiarity. However, the introduction of .zip domains undermines this trust, as users may not have a clear understanding of which sources are genuine in their appearance and which are potential threats.

## Impact on User Security
### Increased Risk of Malicious Downloads
Users often encounter .zip files in the context of file compression and file sharing. The association of .zip with files can lead users to believe that downloading a .zip file from a .zip domain is safe. However, this assumption can be exploited by threat actors or those who want to distribute malware or malicious files disguised as harmless .zip files. Users who trust .zip domains may unknowingly download and execute harmful content on their devices, compromising their security.

### Confusion and Trust Issues
The introduction of .zip domains adds an extra layer of complexity and confusion to the domain ecosystem. Users may find it difficult to distinguish between legitimate websites using traditional domain extensions and potentially harmful websites with .zip domains. This confusion undermines the trust users place in domain names and can lead to inadvertent interactions with malicious entities.

## Conclusion
While the concept of .zip domains may appear nice for hobbyists, their use presents substantial security risks. The deceptive nature of .zip domains makes users vulnerable to domain spoofing, phishing attacks, and the inadvertent download of content that might not seem malicious but it is. Additionally, the introduction of .zip domains adds confusion to the domain landscape, making it harder for users to differentiate between trustworthy sources and potential threats.

To ensure ones safety and security, it is important for everyone to exercise caution when interacting with .zip domains. Implementing security measures, such as staying vigilant for phishing attempts, using reliable security software, and exercising skepticism when downloading files from .zip domains, researching domains before clicking, can help mitigate the risks associated with this extension. By prioritizing security awareness and adopting proactive security practices ,we can protect ourselves from the potential dangers posed by .zip domains.