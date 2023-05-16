---
description: How to host your data and algorithm NFT assets like a boss 😎
---

# Host Assets

### TL; DR

The most important thing to remember is that wherever you host your asset... it needs to be **reachable & downloadable**. It cannot live behind a private firewall such as a private Github repo! You will need to **use a proper hosting service** - Google Drive won't work!

**The URL to your asset is encrypted in the publishing process!**

More details below!

### Publish. Cool. Things.

**If you want to publish cool things on the Ocean Marketplace, then you'll first need a place to host your assets!** You have SO many options where to host your asset including centralized and decentralized storage systems. Places to host may include: Github, IPFS, Arweave, AWS, Azure, Google Cloud, and your own personal home server (if that's you, then you probably don't need a tutorial on hosting assets). Really, anywhere with a downloadable link to your asset is fine.

In this section, we'll walk you through three options to store your assets: Arweave (decentralized storage), AWS (centralized storage), and Azure (centralized storage). Let's goooooo!

Read on, anon, if you are interested in the nitty gritty of security details!

### Security Considerations

{% embed url="https://media.giphy.com/media/81xwEHX23zhvy/giphy.gif" %}

Through publishing, the URL/TX ID/CID required to access the asset is encrypted and stored as a part of the NFT's [DDO](../../developers/core-concepts/did-ddo.md) on the blockchain. Buyers don't have access directly to this information, but they interact with the [Provider](https://github.com/oceanprotocol/provider#provider), which decrypts it and acts as a proxy to serve the asset. The DDO only stores the location of the file, which is accessed on-demand by the Provider. Implementing a security policy that allows only the Provider to access the file and blocks requests from other unauthorized actors is recommended. One of the possible ways to achieve this is to **allow only the Provider's IP address to access the data**. But, not all hosting services provide this feature. **So, you must carefully consider the security features while choosing a hosting service.**

⚠️  **Please use a proper hosting solution to keep your files.** Systems like `Google Drive` are not specifically designed for this use case. They include various virus checks and rate limiters that prevent the `Provider` to download the asset once it was purchased.



