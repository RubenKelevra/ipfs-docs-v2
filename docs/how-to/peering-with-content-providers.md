---
title: Peering with content providers
description: Optimize retrieval speed by making direct connections to large content providers.
---

# Peering with content providers

IPFS allows you to request data from any IPFS node with a copy using the data's [CID][cid-explainer] or content identifier. This process usually involves a lookup on the [distributed hash table][dht-explainer] and may also require establishing new connections to the nodes storing the content.

If you're running an IPFS node that serves many requests, like a public HTTP gateway, for example, you may be able to speed up queries by maintaining long-lived connections to nodes that provide a large volume of data.

Prioritizing connections to certain peers is called **Peering**, and you can tell IPFS which peers to prioritize by editing the [`Peering` configuration][docs-peering-config] in your IPFS config file.

To _peer_ with nodes from Cloudflare, you could update your config to include a `Peering` section like that consists of the ID and addresses for their node:

```json
{
  "Peering": {
    "Peers": [
      {
        "ID": "QmcfgsJsMtx6qJb74akCw1M24X1zFwgGo11h1cuhwQjtJP",
        "Addrs": ["/ip6/2606:4700:60::6/tcp/4009", "/ip4/172.65.0.13/tcp/4009"]
      }
    ]
  }
}
```

::: tip
Generally speaking, users running IPFS at home won't need to set up peering and can ignore this page!

Peering is most helpful for nodes that have a lot of concurrent connections since it prevents the [connection manager][docs-connmgr] from dropping connections it thinks aren't "useful" any longer. If you find yourself running near the connection manager's limit, you may benefit from peering with content providers.
:::

## Content provider list

Below is a community-maintained list of platforms that provide a lot of content to the IPFS network.

If you're running a public IPFS gateway, you may see improved performance for popular queries by adding these nodes to your [Peering configuration][docs-peering-config].

To have your platform added to this list, please [open a PR to edit this page](https://github.com/ipfs/ipfs-docs/edit/main/docs/how-to/peering-with-content-providers.md) and add yourself to the list in alphabetical order.

### Cloudflare

| Peer ID | Addresses |
| ------- | --------- |
|`QmcfgsJsMtx6qJb74akCw1M24X1zFwgGo11h1cuhwQjtJP`|`/ip6/2606:4700:60::6/tcp/4009` <br/><br/>`/ip4/172.65.0.13/tcp/4009`|

### Estuary

| Peer ID | Addresses |
| ------- | --------- |
|`12D3KooWCVXs8P7iq6ao4XhfAmKWrEeuKFWCJgqe9jGDMTqHYBjw`|`/ip4/139.178.68.217/tcp/6744`|
|`12D3KooWGBWx9gyUFTVQcKMTenQMSyE2ad9m7c9fpjS4NMjoDien`|`/ip4/147.75.49.71/tcp/6745`|
|`12D3KooWFrnuj5o3tx4fGD2ZVJRyDqTdzGnU3XYXmBbWbc8Hs8Nd`|`/ip4/147.75.86.255/tcp/6745`|
|`12D3KooWN8vAoGd6eurUSidcpLYguQiGZwt4eVgDvbgaS7kiGTup`|`/ip4/3.134.223.177/tcp/6745`|
|`12D3KooWLV128pddyvoG6NBvoZw7sSrgpMTPtjnpu3mSmENqhtL7`|`/ip4/35.74.45.12/udp/6746/quic`|

### NFT.Storage

See [nft.storage/PEERS](https://github.com/nftstorage/nft.storage/blob/main/PEERS).

### Pinata

| Peer ID | Addresses |
| ------- | --------- |
|`QmWaik1eJcGHq1ybTWe7sezRfqKNcDRNkeBaLnGwQJz1Cj`|`/dnsaddr/fra1-1.hostnodes.pinata.cloud`|
|`QmNfpLrQQZr5Ns9FAJKpyzgnDL2GgC6xBug1yUZozKFgu4`|`/dnsaddr/fra1-2.hostnodes.pinata.cloud`|
|`QmPo1ygpngghu5it8u4Mr3ym6SEU2Wp2wA66Z91Y1S1g29`|`/dnsaddr/fra1-3.hostnodes.pinata.cloud`|
|`QmRjLSisUCHVpFa5ELVvX3qVPfdxajxWJEHs9kN3EcxAW6`|`/dnsaddr/nyc1-1.hostnodes.pinata.cloud`|
|`QmPySsdmbczdZYBpbi2oq2WMJ8ErbfxtkG8Mo192UHkfGP`|`/dnsaddr/nyc1-2.hostnodes.pinata.cloud`|
|`QmSarArpxemsPESa6FNkmuu9iSE1QWqPX2R3Aw6f5jq4D5`|`/dnsaddr/nyc1-3.hostnodes.pinata.cloud`|

### Protocol Labs

| Peer ID | Addresses |
| ------- | --------- |
|`QmUEMvxS2e7iDrereVYc5SWPauXPyNwxcy9BXZrC1QTcHE`|`/dns/cluster0.fsn.dwebops.pub`|
|`QmNSYxZAiJHeLdkBg38roksAR9So7Y5eojks1yjEcUtZ7i`|`/dns/cluster1.fsn.dwebops.pub`|
|`QmUd6zHcbkbcs7SMxwLs48qZVX3vpcM8errYS7xEczwRMA`|`/dns/cluster2.fsn.dwebops.pub`|
|`QmbVWZQhCGrS7DhgLqWbgvdmKN7JueKCREVanfnVpgyq8x`|`/dns/cluster3.fsn.dwebops.pub`|
|`QmdnXwLrC8p1ueiq2Qya8joNvk3TVVDAut7PrikmZwubtR`|`/dns/cluster4.fsn.dwebops.pub`|
|`12D3KooWCRscMgHgEo3ojm8ovzheydpvTEqsDtq7Vby38cMHrYjt`|`/dns4/nft-storage-am6.nft.dwebops.net/tcp/18402`|
|`12D3KooWQtpvNvUYFzAo1cRYkydgk15JrMSHp6B6oujqgYSnvsVm`|`/dns4/nft-storage-dc13.nft.dwebops.net/tcp/18402`|
|`12D3KooWQcgCwNCTYkyLXXQSZuL5ry1TzpM8PRe9dKddfsk1BxXZ`|`/dns4/nft-storage-sv15.nft.dwebops.net/tcp/18402`|

### Storj

| Peer ID | Addresses |
| ------- | --------- |
|`12D3KooWFFhc8fPYnQXdWBCowxSV21EFYin3rU27p3NVgSMjN41k`|`/ip4/5.161.92.43/tcp/4001`<br/>`/ip4/5.161.92.43/udp/4001/quic`<br/>`/ip6/2a01:4ff:f0:3b1e::1/tcp/4001`<br/>`/ip6/2a01:4ff:f0:3b1e::1/udp/4001/quic`|
|`12D3KooWSW4hoHmDXmY5rW7nCi9XmGTy3foFt72u86jNP53LTNBJ`|`/ip4/5.161.55.227/tcp/4001`<br/>`/ip4/5.161.55.227/udp/4001/quic`<br/>`/ip6/2a01:4ff:f0:1e5a::1/tcp/4001`<br/>`/ip6/2a01:4ff:f0:1e5a::1/udp/4001/quic`|
|`12D3KooWSDj6JM2JmoHwE9AUUwqAFUEg9ndd3pMA8aF2bkYckZfo`|`/ip4/5.161.92.36/tcp/4001`<br/>`/ip4/5.161.92.36/udp/4001/quic`<br/>`/ip6/2a01:4ff:f0:3764::1/tcp/4001`<br/>`/ip6/2a01:4ff:f0:3764::1/udp/4001/quic`|

### Textile

| Peer ID | Addresses |
| ------- | --------- |
|`QmR69wtWUMm1TWnmuD4JqC1TWLZcc8iR2KrTenfZZbiztd`|`/ip4/104.210.43.77`|

### Web3.Storage

See [web3.storage/PEERS](https://github.com/web3-storage/web3.storage/blob/main/PEERS).

[dht-explainer]: /concepts/how-ipfs-works/#distributed-hash-tables-dhts
[cid-explainer]: /concepts/content-addressing/#identifier-formats
[docs-peering-config]: /how-to/configure-node/#peering
[docs-connmgr]: /how-to/configure-node/#basic-connection-manager
