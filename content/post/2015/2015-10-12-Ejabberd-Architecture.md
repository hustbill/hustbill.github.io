---
layout: post
title: "Ejabberd-Architecture"
date: 2015-10-12 11:50:00
categories: [技术笔记]
---

Created by Hua Zhang, last modified on Oct 12, 2015  

ejabberd is the de facto XMPP server in the world. ejabberd has been designed from the ground-up, since 2002 for robust, entreprise deployment. The goal has always been to shot for the moon and that what made it a long-lasting success.  
ejabberd is specifically designed for enterprise purposes: it is fault-tolerant can utilise the resources of multiple clustered machines, and easily scale when more capacity is required (by just adding a box/VM).  

Architecture of an ejabberd service
===================================
ejabberd brings configurability, scalability and fault-tolerance to the core feature of XMPP – routing messages.  
Its architecture is based on a set of pluggable modules that enable different features, including:  

    - One-to-one messaging  
    - Store-and-forward (offline messages)  
    - Contact list (roster) and presence  
    - Groupchat: MUC (Multi-User Chat)  
    - Messaging archiving with Message Archive Management (MAM)  
    - User presence extension: Personal Event Protocol (PEP) and typing indicator  
    - Privacy settings, through privacy list and simple blocking extensions  
    - User profile with vCards  
    - Full feature web support, with BOSH and websockets  
    - Stream management for message reliability on mobile (aka XEP-0198)  
    - Message Delivery Receipts (aka XEP-184)  
    - Last activity  
    - Metrics and full command-line administration  
    - and many many more.  

This modular architecture allows high customisability and easy access to the required features. 
ejabberd enables authenticating users using external or internal databases (Mnesia, SQL), LDAP or external scripts.  

We can opt for the storage: 
  
    - SQL databases like Postgres  
    - NoSQL databases like MongoDB

Reference
=========
- [Getting started with ejabberd](https://docs.ejabberd.im/get-started/)
- [ejabberd repo](https://github.com/processone/ejabberd)