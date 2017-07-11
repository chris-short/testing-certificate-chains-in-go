# Golang to the rescue: Saving DevOps from TLS turmoil

Chris Short  
Manager of DevOps at Bankrate  
@ChrisShort  
https://devopsish.com  

## Introduction

Chris Short
Manager of DevOps at Bankrate

* opensource.com and DZone Contributor
* Contributed to The Open Organization Guide to IT Culture Change
* DevOpsDays Speaker and Organizer
* devopsish.com
* chrisshort.net

## But Most Importantly

I'm a Gopher

## Not Too Long Ago in a Place of Work Far, Far Away...

* My team inherited an application
* A third-party constructed this application a few years and had long been abandoned
* Before we could do any re-engineering work, we had to resolve a critical issue.
* **The certificates were about to expire**!

## 2 Chainz

* Let's Talk Certificate Chains
* HTTPS, SSL it's all TLS
* If you are going to use TLS you better have a rock solid configuration for it
* This means you have to include the certificate chain in the correct order
* This is no longer optional in the post-Heartbleed world; the Internets are watching

## This is the Goal

* If you are going to bother to encrypt your traffic you better do it right
* This is what we're aiming for A+
* To get this we need a certificate and the appropriate chain
* Let's get our certificate from a reputable vendor that our company is cool with
* I prefer Let's Encrypt but some folks don't for various reasons
* You generate your CSR and private key
* You send the CSR to the vendor
* The certificate arrives but doesn't have an intermediate key in chain

## NBD ... OMG

* No big deal
* Let's go to the vendor's documentation... And OMG...
* This is when you learn: cryptography is hard but implementing cryptographic best practices might be even harder

## Jackie Chan

* What do we do?
* Look at statistical probabilities and start shuffling keys around?
* The series of games you have to play with openssl or nginx or some other method aren't well known
* The vendor docs are *terrible*
* Don't forget THIS (holds up punch card) was good UX and UI not too long ago

## So what does any good engineer do?

* I needed a tool that would fail if the certificate chain provided was incorrect.
* I wanted a lightweight tool that could be publicly accessible.
* Conducting a third-party analysis of the certificates and configuration was a requirement.
* There were no tools that I could find meeting this need, so I decided to build my own.
* With Go of course!

## Three Go Packages: log, crypto/tls, and net/http

* log
* crypto/tls
* net/http

