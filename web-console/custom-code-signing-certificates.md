# Custom Code-Signing Certificates

## Signing the MBS Windows Client With a Custom Certificate

### Introduction

A code-signing certificate represents a digital record issued by a certificate authority. This certificate verifies that the code has not been modified or corrupted since it was signed and thus provides an extra layer of trust for both the developer and the user. The certificate also maintains integrity of the software publisher all the way from the download site to a user's computer. If the app were somehow tampered with after being published, the certificate would detect the change and issue a warning during installation.

While the MBS Windows client is shipped with a default certificate, MBS providers do have the option to sign the MBS Windows client with a custom certificate. This might be useful for white-label purposes to ensure that each aspect of the software is marked by the provider’s branding.

### The Default Certificate of the MBS Windows Client

By default, the MBS Windows client is signed by a certificate issued by the trusted \_**\*\*\_certificate authority** COMODO RSA**. This certificate is visible to all of your MBS users who install the software on their computer. It also contains the name of the company to which the certificate was issued. In our case it's** Trichilia Consultants Limited\*\*:

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/screenshot-2018-10-16-at-16.14.17.png)

Whenever a new build of the MBS Windows Client is assembled, it is automatically signed with the certificate displayed above. If this certificate is unsuitable due to rebranding requirements, you can use a custom certificate to sign the MBS Windows client.

### Requesting a Custom Certificate from a Certificate Authority

Custom certificates can be requested from a certificate authority that provides root authority trust level. A certificate authority first verifies your identity and then provides you with a custom certificate featuring your company's name. Certificate authorities provide code-signing certificates on a commercial basis and generally charge you an annual fee for them.

The list of established certificate authorities includes Comodo, Symantec, GlobalSign, and DigiCert.

The first step in acquiring a custom certificate is to contact the chosen certificate authority and request a custom certificate. As part of the identity verification process, you will be instructed to provide identity documents like a listing on [BBB.com](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/web-console/drafts/www.BBB.com) or a Legal Opinion Letter \([sample](https://support.comodo.com/index.php?/Knowledgebase/Article/GetAttachment/1231/1676481)\). The identification process generally takes one to three business days. Once your identity is verified, the certificate authority will issue a custom certificate in the name of your company and send it to you.

When this certificate is in your possession, you can proceed to sign any software solution with it, including the MBS Windows Client.

### Signing the MBS Windows Client with a Custom Certificate

To sign the MBS Windows Client using a custom certificate, follow these three steps:

1. Write an email to the MBS support team with the attached certificate. 
2. Wait for the MBS engineers to implement a custom build assembly for your account.
3. Generate a new MBS Windows client build signed with the custom certificate.

The assembled build will be signed with the provided certificate and the certificate information will be indicated in the installer’s properties. The company’s name will also be displayed in the user account control window during the installation.

This build can subsequently be distributed among users and used like a regular MBS build. Whenever a new version of MBS Windows client is released, simply re-generate the required builds and they will maintain the custom certificate.

**Note**: Set a reminder 60 days or so before your certificate expires and make sure to order an updated certificate from the certificate authority. Send the updated certificate to our support team to avoid build problems as expired certificates cannot be used to sign the Windows installer.

