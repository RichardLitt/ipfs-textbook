# IPFS Textbook
Helping me understand what IPFS is and how it works

This is a document where I will define and explain terms that I don't understand in the IPFS implementation. This is for me at the moment, but if you're keen on helping, please feel free to jump in.

### Ipfs.io
_Descriptive text from the homepage_

> The InterPlanetary File System (IPFS) is a new hypermedia distribution protocol, addressed by content and identities. IPFS enables the creation of completely distributed applications. It aims to make the web faster, safer, and more open.

Questions:
 * Why IPFS? Why InterPlanetary?

 > Answered in the ipfs/ipfs repository, [here](https://github.com/ipfs/ipfs#why-the-name-ipfs). I expected this to be answered in the _About_ page on the website, but that links back to the home page. This is confusing for anyone coming just through the website.
 * What does _hypermedia_ mean?

 > Hypermedia is a non-linear (which can be consumed in any order) medium of information similar to "multimedia", but including hyperlinks. An example is the World Wide Web (Internet + DNS + URLs + Servers) which can offer __audio__,__video__, __text__, __graphics__ and __hyperlinks (URLs)__, just like __IPFS__ can.
 * What is a _protocol_? Is it a technical specification, or the implementation, or both?

 > A Protocol is a set of rules, typically used to solve one or more problems. In Information Technology, the word Protocol is used to refer to the set of rules, its technical specification and its implementation. An implementation of a protocol is a program or part of a program which conforms to the specification of the protocol. A program may implement multiple protocols, and each protocol has a different purpose.
 * What is a _distribution protocol_?

 > A distribution protocol is a protocol which solves the problem of distributing data. Depending on the specific protocols
 * What does _addressed by content and identities_ mean?
 
 > #### Let's take a step back
 > First, let's take a look at classic URLs, like http://google.com. This URL tells your computer to use the __HTTP__ protocol to access __google.com__. Your computer then proceeds to use the __DNS__ protocol to figure out where is __google.com__. When it's done, it creates a connection via the Internet to __google.com__'s __IP__ address. This means that __URLs on the Internet address content by location__ and if the content is moved to another location, the connection won't work and the URL will be useless.

 > #### So what's "addressed by content" mean?
 > __IPFS addresses data by content__ which means that an __IPFS URIs__ (like `/ipfs/QmTkzDwWqPbnAh5YiV5VwcTLnGdwSNsNTn2aDxdXBFca7D/example`) tell your computer __what object you want__ and not __where to get it__. __IPFS__ then figures out how to get the object on its own. This has many advantages:
 > - even if a file is moved, as long as there's at least one computer on the Internet that has it on IPFS, __it's never going to get lost__.
 > - every computer can calculate the address of an object and it's always going to be the same if the object is the same, so __you're always sure that the data you get has not been tampered with__ or when your computer verifies the address, it would get a different one and it would know the content was changed. This also means that if two distinct computers add the same file, it makes no difference to you or IPFS if it's downloaded from one or another.
 > - __if multiple people have the same object, your computer can download it from many sources, speeding up distribution when more people have it__ instead of clogging the server that's trying to send thousands of copies to thousands of machines. IPFS will share object with other computers and other computers will help you get your files faster.

 > #### So what's "addressed by identity" mean?
 > __IPFS can also address data by identity, using IPNS__. This means that each computer running IPFS has an identity. Everything that they do is signed using their credentials. __IPNS makes it possible to have dynamic content in IPFS, for example a web application which can be updated without changing its address!__

 > This works because the application can be referenced with an __IPNS Address__ which tell your computer __the identity of the publisher of the application__. IPFS will then figure out the __IPFS Address__ associated to said identity by the owner of the identity (a.k.a. the publisher). The associated address can only be changed by the publisher. __If a bad guy tries to impersonate a machine he doesn't own, your computer will not trust him because when he tells your computer the wrong IPFS address for an IPNS name, that message won't be signed using the publisher's identity private key because only the publisher has that__. Using __public key cryptography__, __your computer can verify the authenticity of messages coming from other computers__, so as long as the private keys of a publisher aren't stolen, you will be totally safe :)

 * "IPFS enables" suggests that IPFS is a tool; does this mean it is more than a specification, but a suite of tools that can be used?
 > IPFS can be intended as a protocol, a set of protocols or their implementation. So yes, IPFS is also a suite of tools that enable machines and users to take advantage of the protocol.
 * Why _completely distributed_? If they are completely distributed, how do they interface with non-distributed networks (http, etc?)?
 * What is a _distributed application_?
 * Why would this make the web faster?
 * Why would this make the web safe?
 * Why would this make the web more open?

> IPFS is an open source project developed by the team at Interplanetary Networks and many contributors from the open source community.

Questions:
 * Who are Interplanatery Networks? Why does this direct me to Protocol Labs?

  > IPFS is a peer-to-peer distributed file system that seeks to connect all computing devices with the same system of files. In some ways, IPFS is similar to the Web, but IPFS could be seen as a single BitTorrent swarm, exchanging objects within one Git repository. In other words, IPFS provides a high throughput content-addressed block storage model, with content-addressed hyperlinks. This forms a generalized Merkle DAG, a data structure upon which one can build versioned file systems, blockchains, and even a Permanent Web. IPFS combines a distributed hashtable, an incentivized block exchange, and a self-certifying namespace. IPFS has no single point of failure, and nodes do not need to trust each other.

Questions:
 * Is peer-to-peer the same as distributed?
  > #### What is Distributed Networking/Computing
  > __Distributed computing or networking__ refers to a network or computer system where data is distributed on multiple machines.

  > It goes in contrast with __centralized networking__, which uses a single or a small group of centralized server machines, and all data goes through them, never directly between clients. This makes it easier to control authenticity and the network in general, but also exposes a central point of failure (the servers) which when taken down render the network/application useless.

  > #### What is Peer to Peer networking
  > __Peer to Peer (p2p)__ is way to organize data exchange in network applications. It lets every node in the network act as both a client and a server. This is always used in at least partly distributed networks, because a centralized network doesn't make any sense combined with peer to peer. Peer to peer applications are complicated because they have to solve many problems:
  > - __flooding__: what happens if a node starts sending useless data to everyone else, stalling the network?
  > - __authenticity__: how do I know a message is authentic? What if it's forged by a different node? What if my message gets tampered with on the way to its destination?
  > - __privacy__: but if my data goes through all these nodes, who tells me they won't read it?

  > __privacy and authenticity__ are both solved in IPFS and many other networks using __public key cryptography__.
  > __TODO__: how does ipfs handle flooding?

  > #### How does IPFS relate to Peer To Peer and Distributed networking

  > __IPFS is peer to peer__ because every node can use other nodes to get data while also serving data to the network. Of course, a machine may only be used to hold copies of data so that availability is not an issue, but the same machine could also be used by a simple user, enjoying cat pictures and other important content over IPFS, while temporarily keeping a cached copy of his favorite celebrity blog that he read earlier, so that it can be served to other machines.

  > __IPFS is also fully distributed__ because there is no central point of failure. The only non distributed part of the system is the bootstrap node list. The bootstrap node list is the list of nodes that IPFS connects to when it first starts, because it doesn't know anyone else yet! Then, nodes exchange their peer list, and more and more machines are discovered and connected together, strengthening the network. IPFS can remember nodes it connected to in the past, and the bootstrap list can be extended or changed, so it's almost impossible that your node can't get online. IPFS is also able to automatically find other computers running a node in local networks, so __it works even WITHOUT the internet!__

 * What does it mean that IPFS can work even without the Internet? How is it possible?
 * Doesn't the internet already connect all computing devices? What do you mean by _system of files_?
 * What is a BitTorrent swarm.P
 * How do you exhange objects inside of a git repository? What does this mean?
 * What does _high throughput_ mean?
 * What does _content-addressed_ mean?
 * What is _block storage_?
 * How does IPFS prove a model? I thought it was a protocol.
 * What defines the subset of hyperlinks that are _content-addressed_?
 * What is a _Merkle DAG_? What is a _generalised_ one?
 * What is a _blockchain_?
 * What do you mean by _Permanent Web_?
 * What is a _distributed hashtable_?
 * What is an _incentivized block exchange_?
 * What does _self certifying_ mean? What does this mean in the context of a namespace?
 * What is a _namespace_?
 * What are the points of failure? What does this mean?
 * What is a node? Why would I expect them to trust each other?

## Glossary

* **Hypermedia**: "Hypermedia, an extension of the term hypertext, is a nonlinear medium of information which includes graphics, audio, video, plain text and hyperlinks." ([Wiki](https://en.wikipedia.org/wiki/Hypermedia)) The key to understanding _hypermedia_ as opposed to normal _media_ is the hyperlinks, which are interactive pointers. Nonlinear simply means it's not meant to be read in a line, like a novel, but can be accessed and perused at random locations.
