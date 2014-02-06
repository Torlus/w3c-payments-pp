## Introduction


## Digital wallets and distributed models generalization

In this chapter, we will make a tour of the most common payment scenarios. 

Then we will make some proposals to provide a more uniform payment processing scheme, so that the user experience feels more comfortable.

Based on this work, we will envision some work-arounds for exisitng payment methods, and discuss on how Web standards could accelerate the migration.

### Card processing

#### State of the art

Let's review the steps of a Visa/MasterCard e-commerce payment:
* The cardholder provides his card details to the acceptor.
* These details, along with transaction information (amount, currency) are relayed to the issuer through the acceptor for 3-D Secure authentication. 
* As a whole, the same information is relayed through the acceptor and the acquirer to the issuer for authorization.

The first step assumes that the cardholder is ready to trust the acceptor at some level.

The second step which is ultimately important, as it is designed to provide a strong authentication of the cardholder, can be bypassed. 

Choosing to not use 3-D Secure is often a decision of the acceptor, that has to put in balance the risk of a void sale, compared to the risk of a fradulent transaction. Again, this is a matter of trust level.

Finally, the third step feels rendundant with the second step, information-wise.

The first step is basically *flawed at Web scale*.

Althought it has its justifications for retail transactions processing, from which the e-commerce model is based upon, this step feels unnecessary and rises many security concerns.

#### Proposed alternative

Another way to envision this payment could be:
* The acceptor provides some identification information, as well as transaction details to the cardholder.
* The cardholder authenticates himself to the issuer and provides transaction details.
* Authorization is performed at issuer level, and its result is handed back to the acceptor through the acquirer.

The advantages of this scheme, besides the fact that it feels more natural, is that the trust environments are already there, as the cardholder only has to trust the issuer, and the same applies to the acceptor and the acquirer.

### Asymmetry concerns

Running an e-commerce business still requires in most cases the subscription of an acceptor contract and a dedicated account for card processing (with the notable exception of PayPal).

Those make the process of receiving money through most debit and credit cards a complicated one, compared to the ease of subscription and use of these cards.

Digital currencies don't suffer from these issues, and it can be stated that perfect symmetry is not only built-in, but also a requirement for them to work.

Lately, initiatives have come to light, as some markets are emerging, and the focus of established financial institutions on small businesses and individuals makes us envision a unprecedented growth in payments.

E-commerce payments for sure, but also in retail, as the mobile point-of-sale (mPOS) solutions allow the same category of merchants to accept cards.

To sump up, what can be foreseen about Web payments is that in years to come, anyone will be concerned about them not only as a customer, but as a seller as well.

## Beyond the wallet scheme

Users of digital currencies are familiar with the idea of digital wallets. These wallets can be used for both selling and purchasing goods and services, and are based on public key cryptography.

Our proposal is to extend the same wallet concept to include both existing payment methods and acceptance means, providing a single local entity to manage both centralized and distributed schemes.

Such a wallet could be shared among different devices: desktops, laptops, smartphones, tablets, etc. but also on servers.

Depending on the use cases of the public key, it may be signed by a Certificate Authority, or using a "Web of trust" scheme instead.

### Use case

#### Initialization
Alice owns an account at Bank A, which provided her also a credit card.

Alice provided a public key to Bank A, and after some identity verification, Bank A signed this public key.

Alice also owns some coupons from Company C, and owns a public key signed by the same entity.



Bob runs an e-commerce store. Bank B provided him an account, as well as an acceptor contract.

Bob provided a public key to his bank, and after some identity verification, Bank B signed this public key.

Bob's store accepts coupons from Company C, therefore one of Bob's public key has been signed by the same entity.

#### Payment process

Alice shops at Bob's store. On checkout, Bob's server provides a set of public keys related to his acceptance capabilities, as well as list of accepted payment methods, an amount, a currency, and a transaction identifier.

Alice's browser displays the available payment methods providers, namely Company C and Bank A.

Alice chooses Company C. The coupon itself is stored in the wallet, so it could be handed back directly to Bob's store.

Alice then chooses Bank A. Bank A identifies Alice, due to her signed public key. An additional authentication step is then performed by Bank A. Upon success, Alice chooses her credit card.

Bank A performs the authorization based on information provided by Bob's store (this information is digitally signed by Bob's private key).

Bank A relays the authorization result to Bank B, which itself relays the result to Bob's server.

### Distributed private key management

