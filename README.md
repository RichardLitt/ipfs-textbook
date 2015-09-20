# IPFS Textbook
Helping me understand what IPFS is and how it works

This is a document where I will define and explain terms that I don't understand in the IPFS implementation. This is for me at the moment, but if you're keen on helping, please feel free to jump in.

### Ipfs.io
_Descriptive text from the homepage_

> The InterPlanetary File System (IPFS) is a new hypermedia distribution protocol, addressed by content and identities. IPFS enables the creation of completely distributed applications. It aims to make the web faster, safer, and more open.

Questions:
 * Why IPFS? Why InterPlanetary? _Answered in the ipfs/ipfs repository, [here](https://github.com/ipfs/ipfs#why-the-name-ipfs). I expected this to be answered in the _About_ page on the website, but that links back to the home page. This is confusing for anyone coming just through the website. 
 * What does _hypermedia_ mean?
 * What is a _distribution protocol_?
 * What is a _protocol_? Is it a technical specification, or the implementation, or both?
 * What does _addressed by content and identities_ mean?
 * "IPFS enables" suggests that IPFS is a tool; does this mean it is more than a specification, but a suite of tools that can be used?
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
 * Doesn't the internet already connect all computing devices? What do you mean by _system of files_?
 * What is a BitTorrent swarm.
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