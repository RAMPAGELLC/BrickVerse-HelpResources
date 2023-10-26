# Complying with Advertising Standards

## Overview

BrickVerse's advertising standards are designed to promote a more transparent, secure, and respectful experience for users, advertisers, and creators of advertising content. These standards collectively contribute to cultivating a positive environment on the platform, encompassing the type of ad content users can engage with, how they can identify it as an ad, and whether they can view ads at all.

These advertising standards are applicable to every advertisement on BrickVerse, whether it's served by BrickVerse or independently published. However, if you opt to independently release advertising content beyond BrickVerse's advertising products, the responsibility falls on you as the ad publisher to ensure that your ad content aligns with these policies. This includes adherence to BrickVerse's Terms of Use, Community Standards, Independent Advertising Policy, and Advertising Standards, as well as compliance with relevant laws and regulations in different regions.

This guide provides a comprehensive overview of the requirements concerning content, disclosure, data privacy, user safety, and the overall integrity of the advertising system that must be met for your ads to run on BrickVerse. These requirements encompass:

* Ensuring your advertising content exclusively features material in line with our policies.
* Clearly indicating that your content is advertising.
* Concealing, replacing, or blocking ads from users who are not eligible to view them.
* Interacting with the advertising system with honesty and integrity, whether as a publisher or advertiser.
* Abstaining from the use of third-party advertising services.

Failure to comply with any of these advertising standards may result in the suspension of your experience and/or account.

**Content Requirements**

For the safety and well-being of all BrickVerse users, it is imperative that your ads only consist of content that does not expose them to hazardous, illegal, deceptive, or otherwise detrimental products, services, or messaging. For instance, ad content must not include any elements of child endangerment, violence, or personally identifiable information, as this would constitute a direct violation of BrickVerse's advertising standards.

\
**Data Privacy Requirements**

Preserving user privacy and enhancing their experience on the platform is of paramount importance. It is crucial that you maintain complete control over independent ad content within your experiences. This entails not serving ad content that you did not directly upload within your BrickVerse experiences. Additionally, it is prohibited to introduce code into your experiences that triggers programmatic calls to third-party ad servers, even for analytics purposes.

**User Safety Requirements**

By maintaining absolute control over your independent ad content, you can implement essential measures to safeguard users from ad content that may not be suitable for them. To determine when these protective measures are necessary, you should utilize `PolicyService:GetPolicyInfoForPlayerAsync`, which provides a dictionary of values that determine whether specific aspects of the experience need adjustments for each unique user. One of the entries within the policy information is "`AreAdsAllowed`," a boolean that indicates whether a user is eligible to view ads. If "`AreAdsAllowed`" returns true, ads can remain visible. However, if it returns false, you must incorporate additional logic to hide, replace, or block the ads to prevent those users from interacting with the ad content.

To illustrate this, consider the following scenarios in an experience where a non-playable character's dialog text serves as an ad. The first scenario presents the ad text displayed to users eligible to view ads, while the second scenario showcases replacement text for users who are ineligible to see ads. By utilizing the "`AreAdsAllowed`" boolean, the experience creator can programmatically verify user eligibility for ad viewing and adapt the ad content context accordingly to cater to each user's specific requirements.

**Ad System Integrity Requirements**

If your experience contains advertising content, whether it's served by BrickVerse or is independently published, you are considered an ad publisher. As an ad publisher, it is imperative that you interact with the ad system in an ethical and transparent manner. This means refraining from any form of abuse or misuse of the ad system, including:

* Exploiting bots or orchestrating large-scale ad engagement campaigns to generate deceptive impressions for ads.
* Falsely categorizing experience metadata to artificially increase ad delivery to users.
* Concealing disclosures in a manner that misleads users into thinking they are engaging with non-advertising content.

Engaging in any of these actions may lead to BrickVerse suspending your experience and/or account, and may also involve the revocation of any ad payouts related to fraudulent impressions or traffic directed to your experience. For additional details, please refer to the Publisher Integrity section of the Advertising Standards.
