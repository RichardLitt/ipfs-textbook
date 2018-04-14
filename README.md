# IPFS Textbook

**Notice: This repo is old, and is not actively being updated. However, if you're keen to edit, please do so!**

Helping me understand what IPFS is and how it works

This is a document where I will define and explain terms that I don't understand about IPFS. This is not necessarily the best place for answering questions about IPFS; if you have questions that you want answered by knowledgeable people, I'd suggest either [ipfs/ipfs](https://github.com/ipfs/ipfs), [ipfs/faq](https://github.com/ipfs/faq), [ipfs/support](https://github.com/ipfs/support), or [ipfs/go-ipfs](https://github.com/ipfs/go-ipfs). This document is for me; it is where I will ask questions I do not know the answer to, and search to answer them on my own, providing **non-technical answers** as much as possible.

My goal is to eventually make a textbook on what IPFS is, how crypto works, what the distributed net would look like, and how to get caught up and knowing enough to be able to contribute on one's own.

_tl:dr; Explain IPFS like I am 5._

### Contribute

If you have questions about IPFS, too, and you want a place to get a really in-depth answer about what things are, add those questions here by [opening an issue](https://github.com/RichardLitt/ipfs-textbook/issues/new). If you know answers and don't mind me (or other contributors!) asking long, exhaustive questions about what the words you use mean, please answer questions!

We will eventually need to split this into chapters and sections. For now, feel free to dive in. Work should mainly happen in the [issues](https://github.com/RichardLitt/ipfs-textbook/issues); once an issue is answered, summarize it and add it to this README in a PR.

_Note: This is very much a work in progress! Currently switching from PR to Issue question and answer._

## Table of Contents

[Contribute](#contribute)  
[Ipfs.io](#ipfsio)  

### Ipfs.io
_Descriptive text from the homepage_

> The InterPlanetary File System (IPFS) is a new hypermedia distribution protocol, addressed by content and identities. IPFS enables the creation of completely distributed applications. It aims to make the web faster, safer, and more open.
>
> IPFS is an open source project developed by the team at Interplanetary Networks and many contributors from the open source community.
>
> IPFS is a peer-to-peer distributed file system that seeks to connect all computing devices with the same system of files. In some ways, IPFS is similar to the Web, but IPFS could be seen as a single BitTorrent swarm, exchanging objects within one Git repository. In other words, IPFS provides a high throughput content-addressed block storage model, with content-addressed hyperlinks. This forms a generalized Merkle DAG, a data structure upon which one can build versioned file systems, blockchains, and even a Permanent Web. IPFS combines a distributed hashtable, an incentivized block exchange, and a self-certifying namespace. IPFS has no single point of failure, and nodes do not need to trust each other.

#### Why IPFS? Why InterPlanetary?

Answered in the ipfs/ipfs repository, [here](https://github.com/ipfs/ipfs#why-the-name-ipfs):

> The original name was GFS, which stood for the Global File System and seemed more accurate than GitFS. But that exact name was already [taken](http://en.wikipedia.org/wiki/GFS2). So I switched Global for Galactic, in an homage to Licklider's [Intergalactic Computer Network](http://en.wikipedia.org/wiki/Intergalactic_Computer_Network), and because peer-to-peer systems look like galaxies to me. But GFS caused confusion with yet another [GFS](http://en.wikipedia.org/wiki/Google_File_System), even though that one is not even open source.

> By popular demand (there were votes and a pronouncement of "GFS is dead. Long live IPFS!" and everything), I switched it to IPFS - InterPlanetary File System, which has several nice properties:

> - IP evokes the goal better: internet infrastructure
> - InterPlanetary still pays a weaker homage to Licklider
> - [If all](http://github.com/ipfs/ipfs/issues) [goes well](http://spacex.com), it may some day actually be InterPlanetary.
> - Name clashes less.

#### What does _hypermedia_ mean?

Hypermedia is a non-linear (as in, it can be consumed in any order) medium of information similar to "multimedia", but including hyperlinks. An example is the World Wide Web (Internet + DNS + URLs + Servers) which can offer audio, video, text, graphics and hyperlinks (URLs), just like IPFS can.

#### What is a _protocol_? Is it a technical specification, or the implementation, or both?

A Protocol is a set of rules, typically used to solve one or more problems. In Information Technology, the word Protocol is used to refer to the set of rules, its technical specification and its implementation. An implementation of a protocol is a program or part of a program which conforms to the specification of the protocol. A program may implement multiple protocols, and each protocol has a different purpose.

#### What is a _distribution protocol_?

A distribution protocol is a protocol which solves the problem of distributing data. A networking protocol can be generic or specialize in different use cases or for different kinds of applications.

#### What does _addressed by content and identities_ mean?

Let's take a step back.  

First, let's take a look at classic URLs, like http://google.com. This URL tells your computer to use the HTTP protocol to access google.com. Your computer then proceeds to use the DNS protocol to figure out where is google.com. When it's done, it creates a connection via the Internet to google.com's IP address. This means that URLs on the Internet address content by location and if the content is moved to another location, the connection won't work and the URL will be useless.

#### So what's _addressed by content_ mean?

IPFS addresses data by content which means that IPFS URIs (like `/ipfs/QmTkzDwWqPbnAh5YiV5VwcTLnGdwSNsNTn2aDxdXBFca7D/example`) tell your computer what object you want and not where to get it. IPFS then figures out how to get the object on its own. This has many advantages:
 - even if a file is moved, as long as there's at least one computer on the Internet that has it on IPFS, it's never going to get lost.
 - every computer can calculate the address of an object and it's always going to be the same if the object is the same, so you're always sure that the data you get has not been tampered with or when your computer verifies the address, it would get a different one and it would know the content was changed. This also means that if two distinct computers add the same file, it makes no difference to you or IPFS if it's downloaded from one or another.
 - if multiple people have the same object, your computer can download it from many sources, speeding up distribution when more people have it instead of clogging the server that's trying to send thousands of copies to thousands of machines. IPFS will share object with other computers and other computers will help you get your files faster.

#### So what's _addressed by identity_ mean?

IPFS can also address data by identity, using IPNS. This means that each computer running IPFS has an identity. Everything that they do is signed using their credentials. IPNS makes it possible to have dynamic content in IPFS, for example a web application which can be updated without changing its address!

This works because the application can be referenced with an IPNS Address which tell your computer the identity of the publisher of the application. IPFS will then figure out the IPFS Address associated to said identity by the owner of the identity (a.k.a. the publisher). The associated address can only be changed by the publisher. If a bad guy tries to impersonate a machine he doesn't own, your computer will not trust him because when he tells your computer the wrong IPFS address for an IPNS name, that message won't be signed using the publisher's identity private key because only the publisher has that. Using public key cryptography, your computer can verify the authenticity of messages coming from other computers, so as long as the private keys of a publisher aren't stolen, you will be totally safe :)

#### "IPFS enables" suggests that IPFS is a tool; does this mean it is more than a specification, but a suite of tools that can be used?

IPFS can be intended as a protocol, a set of protocols or their implementation. So yes, IPFS is also a suite of tools that enable machines and users to take advantage of the protocol.

#### Why _completely distributed_? If they are completely distributed, how do they interface with non-distributed networks (http, etc?)?

IPFS can interface with HTTP because each node can expose an HTTP gateway. Now you can tell your machine where the gateway is using HTTP (for example http://gateway.ipfs.io) then you tell the gateway what object you want to get from IPFS or IPNS (for example http://gateway.ipfs.io/ipfs/QmTkzDwWqPbnAh5YiV5VwcTLnGdwSNsNTn2aDxdXBFca7D/example). This way your machine contacts the gateway (at gateway.ipfs.io) and then the machine running the gateway can fetch the data from IPFS for you and reply over HTTP. Of course the _path_ from your machine to the gateway still uses HTTP and not IPFS, but this allows compatibility with applications and systems that don't support IPFS yet.

Gateways could be built for any protocol, but since pretty much everything can interface over HTTP, HTTP is enough for now.

#### What is a _distributed application_?

A _distributed application_ is a network application that uses _distributed networking_ to store information and communicate with other instances of the application and thus doesn't require any centralized system or infrastructure to work. An example of a popular distributed application is any BitTorrent client such as qBittorrent or Vuze.

#### Why would this make the web faster?

Imagine a classroom with twenty students, their laptops and the professor, who wants to share a 50 MB Video with the class. The professor has many options:

1. he could pass a USB drive around with the file if he has a local copy
2. if the video is already on YouTube or any other website, he could just tell the link to the students. If it's not, he could use his computer and the super slow school network to upload his local copy to Dropbox or Youtube or any other file/video hosting service
3. if he has a local copy, he could create a file/media server on his machine and tell the address to the students (uh! Complicated!)

Option 1 and 3 are too cumbersome, but option 2 is so slow! Imagine 20 students downloading a 50 MB file at the same time from Dropbox or Youtube or anywhere else on the Web!

- The source website would need to upload 50*20 MB = 1 GB of data to the school!
- Since the school has a 20 mbit/s download bandwidth (remember 20 mbits means 2.5 MBytes and ISPs always advertise mbits)
- considering the hundreds of other students may be, very optimistically, only using 50% of that bandwidth we are left with a 1.25 MBytes/s download speed.
- at 1.25 MBytes/s, it would take 13 hours and twenty minutes to download everything. Even at full speed it would still take more than 6 hours!

The good news is that IPFS solves all this.

1. the teacher should add the file to IPFS (which takes at most half a minute) if he has a local copy
1. then, the teacher gives the IPFS link to the students by showing it on a projector or something like that.
1. in a few seconds, the students can type the link and start downloading
1. if the teacher has added a local copy of the video to IPFS using his computer, the students will finish downloading it in a moment because their IPFS node will download the data from the teacher's computer directly, without even going through the web.
1. if there is no one with a local copy on IPFS in the school, the file will be downloaded from someone on the Web, but since IPFS downloads file from the best, closest source, once 1 person has it the file will be shared locally without even going through the Web. By estimating that the total data downloaded is about a hundred MBytes to get the video via IPFS (assuming no one had it locally), we are being pessimistic!

Also when you download a file from the Web, IPFS can and will download it from multiple sources at the same time to speed up the download as much as possible.

#### Why would this make the web safe?

IPFS uses _content based addressing_ (you can find out what it means the appropriate answer) which in short means that IPFS links tell your computer what data you want, and not where it is. When you download the data from another node, your computer can calculate the address of the downloaded data on its own, so that if it doesn't match what you requested, it knows it's not authentic.

IPNS records are also signed using _public key cryptography_, so that your computer can verify on its own that an IPFS publication was actually published by the node with the ID written in the publication.

In short: no one can tamper with the data, and no one can impersonate anyone else unless the victim's private keys were stolen.

#### Why would this make the web more open?

Anyone (in this case Bob) can serve and host his websites/files/data using IPFS, even on an old computer or a slow and limited connection. Once many people have local copies of the data on their nodes, they will help seed the data so that other people can download it faster, even if Bob has shut down his node.

#### Who are Interplanatery Networks? Why does this direct me to Protocol Labs?

#### Is peer-to-peer the same as distributed?
#### What is Distributed Networking/Computing

Distributed computing or networking refers to a network or computer system where data is distributed on multiple machines.

It goes in contrast with centralized networking, which uses a single or a small group of centralized server machines, and all data goes through them, never directly between clients. This makes it easier to control authenticity and the network in general, but also exposes a central point of failure (the servers) which when taken down render the network/application useless.

#### What is Peer to Peer networking

Peer to Peer (p2p) is way to organize data exchange in network applications. It lets every node in the network act as both a client and a server. This is always used in at least partly distributed networks, because a centralized network doesn't make any sense combined with peer to peer. Peer to peer applications are complicated because they have to solve many problems:
  - flooding: what happens if a node starts sending useless data to everyone else, stalling the network?
  - authenticity: how do I know a message is authentic? What if it's forged by a different node? What if my message gets tampered with on the way to its destination?
  - privacy: but if my data goes through all these nodes, who tells me they won't read it?

  privacy and authenticity are both solved in IPFS and many other networks using public key cryptography.
  TODO: how does ipfs handle flooding?

#### How does IPFS relate to Peer To Peer and Distributed networking

IPFS is peer to peer because every node can use other nodes to get data while also serving data to the network. Of course, a machine may only be used to hold copies of data so that availability is not an issue, but the same machine could also be used by a simple user, enjoying cat pictures and other important content over IPFS, while temporarily keeping a cached copy of his favorite celebrity blog that he read earlier, so that it can be served to other machines.

IPFS is also fully distributed because there is no central point of failure. The only non distributed part of the system is the bootstrap node list. The bootstrap node list is the list of nodes that IPFS connects to when it first starts, because it doesn't know anyone else yet! Then, nodes exchange their peer list, and more and more machines are discovered and connected together, strengthening the network. IPFS can remember nodes it connected to in the past, and the bootstrap list can be extended or changed, so it's almost impossible that your node can't get online. IPFS is also able to automatically find other computers running a node in local networks, so it works even WITHOUT the internet!

#### What does it mean that IPFS can work even without the Internet? How is it possible?

IPFS will announce its presence over its local network, so that other computers running IPFS can receive the message and connect to your machine. This means that IPFS is able to automatically build a local network if the computers are all in the same LAN and can communicate. So if a file is requested and in the LAN someone has it, it will still work. Services such as an Instant Messaging service (think whatsapp) built on IPFS will still let you chat with people on your LAN if the Internet is not avaikable.

This also means that IPFS could be adapted to run over any kind of communication channel, for example Bluetooth.

#### Doesn't the internet already connect all computing devices? What do you mean by _system of files_?
The Internet does make it possible for every computer to communicate (sometimes not directly due to issues such as NAT) but it doesn't mean they automatically do. On the Web, your computers only connects to another if you tell it to, so if you want to see a website you have to tell your computer where the website is.

IPFS is built on top of the Internet and uses it to automatically find other computers running IPFS and automatically connects with them. When you need something, you don't tell IPFS where it is, you actually tell what you want by providing the object hash (think of it like a fingerprint of the file/folder/app you want) and IPFS asks his peers until someone has it, then retrieves it for you. This has many advantages, better detailed in the answer to the _What does addressed by content and identities mean?_ question.

TODO: what does _system of files_ mean?

#### What is a BitTorrent swarm?
#### How do you exhange objects inside of a git repository? What does this mean?
#### What does _high throughput_ mean?
#### What is _block storage_?
#### How does IPFS prove a model? I thought it was a protocol.
#### What defines the subset of hyperlinks that are _content-addressed_?
#### What is a _Merkle DAG_? What is a _generalised_ one?
#### What is a _blockchain_?

A blockchain is a specific kind of distributed database, which could also be built over IPFS. You can think of a block chain as a huge stack of papers one on top of another. When you want to make a change to the database, you just add a paper on top that describes what are the changes that you are doing.

This system is useful in distributed networks that share a database, like the Bitcoin network. You can't double spend bitcoins (obviously) but why is that? How is it possible? If they're digital, we can't we copy them and make more?

There are no bitcoins, actually. There is only a blockchain, and when Joe places a signed document on top of the blockchain saying that he wants to move this 50 bitcoins to Amazon's wallet to buy a new video game, it won't work because all the nodes in the network will check if the transaction is valid and of course, by looking at all other documents, it's clear that Joe only has 10 bitcoins based on how many were added and/or removed from his wallet. So the network agrees that the document is not valid and won't accept it in their copy of the blockchain, invaliding the transaction. Meanwhile, Alice successfully moves some funds, so all the other nodes see that the transaction is valid and they copy it on top of their blockchain.

Thus, the chain grows, and the network keeps functioning, even though nodes can't trust each other. No one can impersonate you on the blockchain, because transactions where _you_ send money have to be signed by your wallet using public key cryptography.

#### What do you mean by _Permanent Web_?

Since IPFS is content addressed (see _what does content-addressed mean?_ answer), every copy of the same file produces the same address when added to IPFS. So as long as there is at least one little computer with one copy of the file and a connection to other computers running IPFS, the file will be available. If Joe is hosting his blog from home and the electric company shuts down his electricity because Joe is broke, his fans will still be able to view the website (unless he didn't use IPFS. Way to go, Joe) because someone, somewhere will have a copy of it since they viewed it recently and the address will be the same because the content is the same.

#### What is a _distributed hashtable_?

An hashtable is a table with two columns and a row for every object. The first column is the identifier (usually an hash but not always), used to identify the data in the second column. Using this _hashtable_, nodes can find the correct object when other nodes give them the identifier.

An hash is a little piece of data, like `QmTkzDwWqPbnAh5YiV5VwcTLnGdwSNsNTn2aDxdXBFca7D`, that is calculated mathematically from another piece of data, and it represents its fingerprint.

- when two computers calculate the hash of the same identical file or the same identical message, the hash _will always_ be the same identical hash, but if the data is even slightly different, the hash will be completely different.
- this means that unless an hashtable is used, there is no way to get the original content from having just the hash (hashing is irreversible).
- it's also borderline impossible that two different pieces of data or files have the same hash.

#### What is an _incentivized block exchange_?
#### What does _self certifying_ mean? What does this mean in the context of a namespace?

Using public key cryptography, nodes can emit signed messages so that other nodes will be certain that those signed messages weren't being tampered with (modifying a signed message makes signature verification fail). This means that nodes can trust data, even if it's coming from someone that is not the original source, as long as it has a valid signature.

#### What is a _namespace_?
#### What are the points of failure? What does this mean?

A _point of failure_ in a network is a machine that when shut down, malfunctioning or compromised in any way, gravely cripples the network often rendering it totally useless until the point of failure starts working as it should again. Imagine twitter's server shutting down right now. In a moment, nobody would be able to read tweets, write tweets or use twitter in any way!

IPFS doesn't have central _points of failure_ because it's decentralized (you can learn more in the answers to questions related to decentralization). The only point of falure in IPFS is the bootstrap nodes: they are the list of the first nodes that your computer connects to when running IPFS. However, once your computer finds more nodes by talking with the bootstrap nodes, it will remember them so that even if the boostrap nodes are not available (almost impossible since they are many, independent machines across the globe), the network still works (but new users wouldn't be able to join). This can be solved by using a bigger bootstrap node list and hardening them to make them stronger against network limits, attacks and vulnerabilities.

#### What is a node? Why would I expect them to trust each other?

A node is a machine running IPFS. It could be a standard desktop computer, a laptop, a mobile device, anything that can run programs and connect to a network really. Nodes never trust each other unless there is mathematical proof that a message, statement or other information is to be trusted: you can learn more by searching mentions of _public key cryptography_ in this textbook and read the contextual answer and question. Anyway, using _public key cryptography_ and _cryptographic hashes_, your node can prove the authenticity and validity of data received from other nodes.

