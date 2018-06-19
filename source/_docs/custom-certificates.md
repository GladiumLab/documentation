---
title: Custom Certificates on the Global CDN
description: @ari-gold FEEEED ME
---

A white glove Custom Certificate Concierge Service in now available and **limited to  Legacy SSL Customers with a Pantheon contract**, including **Enterprise**, **EDU+**, **Pantheon One**, **Elite** and **Reseller** customers. If your site was purchased online via the Site Dashboard and you’d like access, [let us know](@ari-gold FEEEEEED ME), and we’ll let you know if it becomes available.

## Eligibility

Access to this service is limited to existing Legacy SSL customers with a Pantheon contract.

## Why upgrade to the Global CDN?

If your site is using our Legacy SSL service it's on deprecated, legacy infrastructure, served from a single server in the central US. When you upgrade to the Global CDN you'll see faster performance, with content  delivered from over 50 points of presence (POPs) around the world.

If your site uses Legacy SSL, it's also on an outdated TLS configuration. The Global CDN is configured to only use TLS 1.2 and no weak 3DES cipher. On the legacy infrastructure, your site isn't as fast, secure, or as resilient as it could be.

## Upgrade to Global CDN with Free & Automated HTTPS

If you just haven’t gotten around to upgrading, consider using our managed HTTPS, which includes automated certificate management, leveraging Let’s Encrypt certificates. As a convenience, when you upgrade to managed HTTPS you’ll never have to worry about an expired certificate again. As long as your domain is pointed to Pantheon, we will automatically renew the certificates required to keep your site secure. [Upgrade](/docs/https/) to get best-in-class encryption and an A+ grade from SSL Labs.

## Upgrade to Global CDN with Manual Custom Certificate

If you have a requirement for a custom, dedicated certificate, you can now bring it the Global CDN.

1. [Open a support ticket](/docs/support/#ticket-support) with the certificate details required to generate a **Certificate Signing Request** (CSR). Use as few certificates as possible. Domains from multiple environments and sites can be combined, with up to 100 [**Subject Alternative Names**](https://en.wikipedia.org/wiki/Subject_Alternative_Name){.external} (SANs) per certificate.

2. Pantheon support will provide you with the CSR file, to pass on to your **Certificate Authority** (CA).


3. Once you have a set of certificates from the CA, send us:

    - The end-client certificate
    - Any intermediate certficates provided by the CA.<br><br>

    Be sure to send these as separate files, not a "chained cert".

4. Update your [DNS](/docs/dns/) records, including `A`, `AAAA`, and [CAA](#add-caa-records) records.


5. Test your new records using tools like `dig` (optional, but strongly recommended).


### Test Before Going Live

Test production domain(s) before updating DNS by overriding DNS on your local computer from your local `hosts` file. For non-production domains, test on any environment (Dev, Test, Live or Multidev), just make sure to include the non-production domains on your certificate.

### Add CAA Records

A **Certification Authority Authorization** (CAA) record is used to specify which certificate authorities (CAs) are allowed to issue certificates for a domain. In order to ensure your custom certificate is served for all traffic, you must prevent Let’s Encrypt from issuing certificates. You have two options to prevent Let’s Encrypt from issuing certificates for domains on your custom certificate:

 - An empty CAA policy,
 - CAA records permitting your CA, but not Let’s Encrypt.

To help generate CAA records, please see the free online tool: <https://sslmate.com/caa/>

## Technical Specifications

|                                                                       | Legacy                    | Global CDN with Let's Encrypt   | Global CDN with a Custom Certificate  |
|:--------------------------------------------------------------------- |:------------------------- |:------------------------------- |:--------------------------------------|
| **Price**                                                             | $60/month per environment | Free                            |                                       |
| **Certificate Type**                                                  | Bring your own            | Shared, issued by Let's Encrypt | Bring your own                        |
| **Renewal**                                                           | Self-managed (up to you)  | Automatic                       | Self-managed (up to you)              |
| **Inbound IP**                                                        | Static (unique)           | Static (shared)                 | Static (shared)                       |
| **Client Support**                                                    | 96.02% of browsers        | 95.55% of Browsers <br>Some very old browsers not supported <sup><a href="https://caniuse.com/#search=TLS%201.2">1 <a href="https://caniuse.com/#search=SNI">2</a></sup> | 95.55% of Browsers <br>Some very old browsers not supported <sup><a href="https://caniuse.com/#search=TLS%201.2">1 <a href="https://caniuse.com/#search=SNI">2</a></sup> * |
| [**SSL Labs Rating**](https://www.ssllabs.com/ssltest/){.external}    | A                         | A+ [with HSTS](/docs/hsts/)     | A+ [with HSTS](/docs/hsts/) *         |
| **Protocol**                                                          | TLS 1.1 & 1.2             | TLS 1.2 with SNI                | TLS 1.2 with SNI                      |
| **Ciphers**                                                           | Weak 3DES Cipher          | No Weak 3DES cipher             | No Weak 3DES cipher                   |
| **Delivery**                                                          | US Datacenter             | [Global CDN](/docs/global-cdn)  | [Global CDN](/docs/global-cdn)        |
| **Encryption Endpoint**                                               | Load Balancer             | Application Container           | Application Container                 |

\* Browser compatibility and SSL Labs score is guaranteed for shared Let’s Encrypt certificates. The same results are typical for a custom certificate from a mainstream CA with mainstream attributes, but not guaranteed.  For custom certificates, compatibility and SSL Labs score depends on attributes of that certificate, such as number of SAN entries, CA and signing algorithm.

## Frequently Asked Questions

### Do I need a separate certificate for each site in my organization?

Nope! You can use the a single certificate to cover multiple domains spread across various environments or sites. This capability is enabled because the Global CDN uses a technology called Server Name Indication (SNI), which automatically matches inbound requests with an appropriate certificate, including custom certificates.

### How long will it take to load my certificate into Pantheon?

Please allow two business days to get a CSR and load the certificate.

### What about for sites purchased online?

Custom certificates are currently available to customers with a Pantheon contract using Legacy SSL. We have no current plans to offer it to Basic or Performance sites. If you pay for your site with a credit card and are interested in using a custom certificate, please [let us know](@ari-gold FEEEEED ME).

### Will custom certificates be self-serve?

The concierge service is designed to quickly guide you through the steps required to deliver HTTPS on the Global CDN using your custom certificate. Due to the limited demand, and infrequent need to load custom certificates, the concierge service may be the best fit, although we are evaluating following up with a self-serve option.


### Which certificates do I submit?

Include the end-client certificate for your named domains, as well as the intermediate certificate, in separate files.


### What is the maximum number of SAN entries?

For the broadest client compatibility we recommend limiting the number of Subject Alternate Names to 100.


### Are private keys available for export?

Private keys are just that, private, and not available for export. They are stored securely, server side, and it’s a security best practice to not share private keys among different deployments. If you manage multiple domains, with some on Pantheon, and some outside of Pantheon, then we recommend using separate certificates, and we are happy to provide you with a new Certificate Signing Request (CSR) so we can deploy a certificate on Pantheon that only has the domains served on Pantheon.


### What are the Global CDN IP addresses?

The Global CDN currently has 4 offsets. After certificate deployment, we will provide DNS information so you can upgrade. In the examples below, `X` will be replaced with a value of `1`, `2`, `3`, or `4`:

A record: `23.185.0.X`
AAAA record 1:  `2620:12a:8000::X`
AAAA record 2:  `2620:12a:8001::X`

**Note:** AAAA records are not required, but recommended as a best practice for performance, especially for mobile devices.
