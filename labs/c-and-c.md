---
Title: Finding Architectural Styles 
Author: nernst
date: Oct 2021

---

# Lab: Architectural Styles

In your group, create a C&C view for a near-field communication payment terminal like Square offers. The terminal connects to a point of sale (POS) system which manages the business's inventory. It handles communication with the customer's phone or card (using passive RFID chip in the card/phone), communicates with an authorization agent (e.g., Royal Bank), and ensures the PoS system is told of the sale. 

1. What architectural style is best suited to this? Pick one of the C&C styles from the notes, see the book chapter 22, or the comprehensive catalog in [Documenting Software Architectures](https://learning-oreilly-com.ezproxy.library.uvic.ca/library/view/documenting-software-architectures/9780132488617/ch04.html), chapter 3 and 4. 
2. Document the style as a diagram on a tablet drawing program or pencil and paper. 
3. Make sure your diagram has a legend!  
4. Make sure your diagram explains all the elements involved. 
5. Add a short description for each of th elements (nodes) in your diagram. 
6. Now, ensure your diagram can easily answer the following quality attribute scenarios:

<!-- > Security: Data in Transit: When the client's card is near the terminal, the card is read by the terminal and the card data is used to authorize the transaction. At no time is the client's data ever exposed to third parties.  -->

Gotchas:

* Not including a legend, including for any colours, line styles, etc. Will the diagram be interpretable on its own?
* Not explaining, in the description below, key attributes of the style such as bus capacity
* Forgetting key runtime elements

<!-- things to look for: reasonable approaches are a shared data or pipe and filter/workflow style. Client server and pub sub are probably not relevant, nor is services. we are interested in talking about how the crypto protocol works. Note: we do not capture behavior or sequence chart style behaviors here: we just show what exists at runtime. Diagrams should show at least the PoS erminal, the NFC terminal, and a client/phone/card. Possibly add in some filters in the PoS terminal, possibly include Royal Bank or authorizer -->
