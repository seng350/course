----
Title: Privacy
Author: Neil Ernst
----

# Privacy as QA

For many software companies, and most business in general, data is now [recognized as a competitive advantage](https://www.youtube.com/watch?v=DtumWOsgFXc). How does Facebook, and others, make money offering you a 'free' service? It sells your data - about your web habits, your friends, even [your menstrual cycles](https://www.theguardian.com/world/commentisfree/2019/sep/14/your-period-tracking-app-could-be-sharing-intimate-details-with-all-of-facebook) - to advertisers. 

> What are the tradeoffs in apps that use this advertising-based approach, from their perspective? 
>
> As a CTO, we would have to balance the revenue generation piece, including our ability to improve our products internally, with the potential fall-out if people's medical or other information was released or obtained. At UVic for example there are strict data protection policies in place. 
>
> It is less clear what financial impact privacy breaches have on for profit companies. A breach of credit cards at Target seems to have [cost about 300 million.](https://www.thesslstore.com/blog/2013-target-data-breach-settled/)

On the positive side, this is a major revenue source: for Facebook and Google, advertising and personal information are the vast majority of their revenue. This arguably allows them to provide benefits, such as free email, free search engines, etc.

Private information is defined to be "any information relating to an individual, whether it relates to his or her private, professional or public life." This is often abbreviated as PII, personally identifiable information. But it is not just about your direct info, like SIN, Address, Height/Weight. 

Think about a table that collected HIV positive individuals [per postal code](https://www.google.com/maps/place/Victoria,+BC+V8X+1E3/@48.4481269,-123.3611602,17z/data=!3m1!4b1!4m5!3m4!1s0x548f738538e8c0e7:0x7f7b3ab51236fb26!8m2!3d48.447995!4d-123.3589658). How many HIV positive records would you need to guarantee anonymity? Even if the individual's name was redacted, there's a good chance we could figure it out by inference (e.g., a nurse stops at that house every day), or by joining it with other records (e.g., amazon purchase history).

Thus an emerging QA has become the need to consider privacy of the people whose data you collect. There are at least three legal frameworks to think about here.

1. In BC, we operate under the Canadian legal framework and the provincial [Personal Information Protection Act](http://www.bclaws.ca/Recon/document/ID/freeside/00_03063_01) (from 2003!). It says things like, among others, I need to provide an alternative if you object to storing your data in the US. 
2. In the States, there is clearly less concern, but that seems to be changing with talk about regulating Facebook and other social media platforms. See [Arvind Narayanan on Twitter](https://twitter.com/random_walker/status/1187391482401038336).
3. In the EU, there is a heavy-duty legal framework called the General Data Protection Regulation or GDPR. It applies to any company processing EU citizen data. 

## GDPR

 If an organization is found to violate the GDPR, the organization could face a maximum fine the greater of either four percent of annual revenue or 20 million euros. 

Reports leading up to the deadline (when the bill became law) show that a significant number of organizations were woefully unprepared for the GDPR. On the official day of GDPR enforcement, many organizations simply shut down violating aspects of their system because there was no other remedy to comply with the GDPR by the deadline.

Like the GDPR, the California Consumer Privacy Act [CCPA](https://www.varonis.com/blog/ccpa-vs-gdpr/) applies to such a large set of companies and individuals that in many cases compliance, regardless of where you live/headquarter is irrelevant. 	

GDPR Mandates:

1. accuracy 
2. data minimization 
3. integrity and confidentiality 
4. lawfulness, fairness, and transparency 
5. purpose limitation 
6. storage minimization 
7. Accountability is often listed as an additional, but separate GDPR principle. 

In addition, the GDPR also bestows a plethora of rights to each data subject, such as 

1. right to be informed, 
2. right to erasure, 
3. right to restrict processing, 
4. right to data portability, and 
5. right to object.  

# Privacy Scenarios

We brainstormed some scenarios. 

- For government IT projects
- For web apps running on Android
- For older websites.

#Privacy Tactics

One thing to emphasize is that it is really hard to add privacy - or security, for that matter - after a breach. Thus, effective design for privacy (or security) is often "build privacy in" from day one. 

There is no existing tactics tree for privacy, so let's create a quick one. 

As input we have (Q) - something like "attempt to obtain PII" and our response should be (Q) "system detects, reacts and repairs breach". See the security tactics in the book, which are similar. We will rely on Hoepman's Strategies book in the following discussion. 

## Data Oriented Strategies

**Minimise** : Limit as much as possible the processing of personal data. 

* Select: define selection criteria and limit processing, e.g. with a white-list. "It does hurt to try"
* Exclude: what won't you store? Consider the case of phone IMEI numbers.
* Strip: Remove data no longer needed as soon as possible. Can you aggregate over time periods? 
* Destroy: Completely remove data when no longer needed. Define policies about this. Ensure the deletion is physical not logical.
* Consider the toll-road example and uniquely identifying cars vs paying in cash.

**Separate**: Separate the processing of personal data as much as possible. 

* Isolate: do the processing in physically different database. Avoid joins.
* Distribute: store the data in distributed locations (pieces of the data, that is: don't store multiple copies). Use the computer of the individual for assembly. 
* Example: a de-centralized social network using P2P. iOS face tracking models. 

**Abstract**: Limit as much as possible the detail in which personal data is processed. 

* Summarize: age categories vs specific ages. [Pattern](https://privacypatterns.org/patterns/Location-granularity)
* Group: group profiles (3rd year SENG) vs individual profiles (danger of assumptions)
* Perturb: add jitter to the data (± some variance parameter) to prevent easy identification. 
* Examples: over/under 19, coarse locations, k-anonymity

**Hide** : Protect personal data, or make it unlinkable or unobservable. Make sure it does not become public or known. 

* Restrict: who can access a table/dataset. Need to know.
* Obfuscate: encrypt and hash both data-at-rest and data-in-transit. https://privacypatterns.org/patterns/User-data-confinement-pattern
* Dissociate: break correlations.
* Mix: recreating an ordering (diagnosis, prescription, purchase drug, purchase refill) can be one way to de-anonymize logs. Mixing the sequence or delaying the reaction can make this harder.
* Examples: TOR, the Onion Router, where you mix the 'middle relays' to obscure the source of the request. See https://privacypatterns.org/patterns/Onion-routing

## Process Oriented Strategies

**Inform**: Inform data subjects about the processing of their personal data in a timely and adequate manner. 

* Supply: have a privacy policy and make your 3rd party partners obvious.	
* Explain: make it clear why you need to process the data.
* Notify: when you need to change policies, access data, or have a breach. https://wiki.mozilla.org/Privacy_Icons
* Example: Apple location services icon colour.

**Control** : Provide data subjects adequate control over the processing of their  personal data. 

* Consent: get permission that is informed.
* Choose: give reasonable alternatives and opt-outs.
* Update: let users easily access the data stored about them. 
* Retract: let people quit the service or retract permission. 
* Example: Google offers periodic reminders about privacy settings and allows people to download their data. 

**Enforce**: Commit to processing personal data in a privacy-friendly way, and adequately enforce this. 

* Create, maintain and uphold organizational approaches to privacy. Ensure it is a first-class concern. Example: log employee access to private data, such as licence plate databases or traffic cameras in BC. See https://privacypatterns.org/patterns/Unusual-activities 

**Demonstrate** : Demonstrate you are processing personal data in a privacy-friendly way. 

* Record, audit and report all activities related to privacy. Audit these activities with an arms-length body (e.g, the BC Privacy Commissioner)

# Exercise

Look through the HomeAssistant source code. Identify 2 examples of PII and privacy scenarios, and see if the developers have done anything to mitigate this (hint: what happens to stored camera footage?) 

# References

1. *Jaap-Henk Hoepman* , 2019. Privacy Design Strategies (The Little Blue Book). 
2. https://privacypatterns.org/patterns/
   3. https://resources.sei.cmu.edu/asset_files/Podcast/2009_016_100_47206.pdf