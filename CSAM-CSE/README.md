# CSAM and CSE Resources
If you suspect a child is in immediate danger in any way, contact the police immediately.

## General Guidance

### Disclaimer
The information provided on this page does not, and is not intended to, constitute legal advice; instead, all information, content, and materials available on this page are for general informational purposes only.  Information on this page may not constitute the most up-to-date legal or other information.  This page contains links to other third-party Web sites.  Such links are only for the convenience of the reader, user or browser; IFTAS and its members do not recommend or endorse the contents of the third-party sites.

Readers of this page should obtain legal advice with respect to any particular legal matter.  No reader, user, or browser of this site should act or refrain from acting on the basis of information on this site without first seeking legal advice from counsel in the relevant jurisdiction.  Only your individual attorney can provide assurances that the information contained herein – and your interpretation of it – is applicable or appropriate to your particular situation.  Use of, and access to, this page or any of the links or resources contained within the site do not create an attorney-client relationship between the reader, user, or browser and Web page authors, contributors, contributing law firms, or IFTAS members and their respective employers. 

### User Generated Content
If you operate an ActivityPub service you are an electronic communications provider and you likely meet the definitions of ESP, ISP, online service provider, and other nomenclature in law that describes electronic communications services. Services that federate with third parties, and/or have their content feeds visible to public users, and/or allow user account creation, are liable for the content they host and display to end users in all jurisdictions.

 - User Generated Content and the Fediverse: A Legal Primer: https://www.eff.org/deeplinks/2022/12/user-generated-content-and-fediverse-legal-primer
 - Notes on operating fediverse services (Mastodon, Pleroma etc) from an English law point of view: https://decoded.legal/blog/2022/11/notes-on-operating-fediverse-services-mastodon-pleroma-etc-from-an-english-law-point-of-view
 - Scaling a public Mastodon instance: Legal, compliance, privacy and more: https://bottomlinelawgroup.com/2023/01/23/mastodon-instance-legal-compliance-privacy/
 - A guide to potential liability pitfalls for people running a Mastodon instance: https://denise.dreamwidth.org/91757.html
 - Combating child sexual abuse online: https://www.europarl.europa.eu/RegData/etudes/BRIE/2022/738224/EPRS_BRI(2022)738224_EN.pdf

## National and Extranational Law
Scroll down in the linked page to review the legality of real/realistic; fictional; and possession in most countries.
 - https://en.wikipedia.org/wiki/Legality_of_child_pornography

### Legal status of fictional pornography depicting minors
Regardless of its legality in a given jurisdiction, if your content is available to end users in a jurisdiction where such content is illegal, you are liable for its availability. 
 - https://en.wikipedia.org/wiki/Legal_status_of_fictional_pornography_depicting_minors

## Detection
Services exist to compare stored media with hashes of known material, and ML-assisted perceptual matches. For the most part, these are heavily restricted and will require your ability to sign legal agreements with the service providers. 

If you are an independent provider and would like to use IFTAS detection services, please fill out this Needs Assessment: https://cryptpad.fr/form/#/2/form/view/thnEBypiNlR6qklaQNmWAkoxxeEEJdElpzM7h2ZIwXA/ 

### CDN
 - Cloudflare CSAM Scanning Tool: https://developers.cloudflare.com/cache/reference/csam-scanning/
 - - Appears to be US-only as it requires NCMEC credentials, which can only be acquired by US entities

### Standalone Platforms
 - Microsoft PhotoDNA: https://www.microsoft.com/en-us/photodna
 - Thorn Safer: https://get.safer.io/csam-detection-tool-for-child-safety
 - Project Arachnid Shield: https://projectarachnid.ca/en/#shield
 - AI Horde csam_checker: https://github.com/Haidra-Org/horde-safety/blob/main/horde_safety/csam_checker.py

### Platform-specific
  - (Lemmy) A script that goes through a lemmy pict-rs object storage and tries to prevent illegal or unethical content: https://github.com/db0/lemmy-safety
  - (Firefish) CloudFlare configuration: https://socialweb.coop/blog/firefish-cloudflare-quickfix-r2-tutorial/

## Reporting
You may be legally required to report CSAM and/or CSE to the authorities. In general, your country of operation is what matters, followed by the country in which you host the media. Exactly what needs to be reported, how quickly, and to whom varies depending on the country and type of provider. In general however,  electronic service providers (this includes all ActivityPub services that are not single-user instances) are not required to actively seek out CSAM, but simply to report it when they are made aware of it. They might become aware of the content because of several things. Examples include performing their own voluntary actions to detect CSAM on their services, or as a result of external parties and service users flagging it to them.

To explore your legal requirements, check the Global Legislative Review in this document: https://cdn.icmec.org/wp-content/uploads/2018/12/CSAM-Model-Law-9th-Ed-FINAL-12-3-18-1.pdf

The "ISP Reporting" column defines your requirements (ISP in this context includes electronic communication service providers)

Be aware that some jurisdictions may require you to store the material for a law enforcement/investigatory purpose, in which case you must have processes in place to securely store and limit access to the material for a set period of time.

#### List of national reporting hotlines
https://support.google.com/websearch/answer/148666?hl=en

If you can't find your country listed, contact INHOPE through their website: https://inhope.org/

## Coping with Exposure
 - Content Moderators’ Strategies for Coping with the Stress of Moderating Content Online: https://tsjournal.org/index.php/jots/article/view/91
 - Coping with Child Sexual Abuse Material Exposure: https://www.nctsn.org/resources/coping-with-child-sexual-abuse-material-exposure
 - Evidence-based strategies to help you complete your stress cycle: https://ideas.ted.com/emotionally-exhausted-burnout-completing-stress-response-cycle/
 - 14 Free and Low-Cost Mental Health Resources: https://captainawkward.com/2017/10/03/guest-post-14-free-and-low-cost-mental-health-resources/

For anyone in the US, UK, CA, or IE: Get support from a crisis counselor from the Crisis Text Line 24/7
 - US: Text HOME to 741741
 - UK: Text SHOUT to 85258
 - CA: Text HOME to 741741
 - IE: Text HOME to 50808

## Moderation Workflow Harm Reduction
Consider using a second browser profile for moderation activities.
 - Painless Peek - a browser extension to make it easier to more safley view traumatic imagery: https://github.com/adacable/painlessPeek
 - Firefox Grayscale - renders images in grayscale to reduce trauma: https://github.com/xpmn/firefox-grayscale

## Research
Child Safety on Federated Social Media: https://purl.stanford.edu/vb515nd6874

## Discussion
 - ActivityPub SocialHub: https://socialhub.activitypub.rocks/t/about-child-safety-on-federated-social-media/3447 
 - ActivityPub FEP WIP: PhotoDNA Attestation extension: https://codeberg.org/fediverse/fep/pulls/140
 - ActivityPub 2023-08-04 Special Topic Call - Social Web and CSAM: Liabilities and Tooling: https://socialhub.activitypub.rocks/t/2023-08-04-special-topic-call-social-web-and-csam-liabilities-and-tooling/3469

