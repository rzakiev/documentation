---
description: >-
  This tutorial we will explain how to sign up for Google Cloud in just a few
  steps.
---

# Signing Up for Google Cloud

To sign up for Google Cloud, go to [https://cloud.google.com/storage/](https://cloud.google.com/storage/) and click **TRY IT FREE**.

![](../../../.gitbook/assets/image%20%2843%29.png)

Agree with their terms of service and fill in the registration form.

![](../../../.gitbook/assets/image%20%284%29.png)

![](../../../.gitbook/assets/image.png)

Once the registration form is complete, click **Start my free trial**. ****

![](../../../.gitbook/assets/image%20%2840%29.png)

Next up you'll see the main dashboard. Proceed to the navigation drawer to create a so-called project.

![](../../../.gitbook/assets/image%20%2837%29.png)

Select **IAM & Admin**.

![](../../../.gitbook/assets/image%20%2818%29.png)

In **Projects**, click **Create Project**.

![](../../../.gitbook/assets/image%20%2838%29.png)

All data in Google Cloud Storage belongs inside a project. A project consists of a set of users, a set of APIs, billing, authentication, and monitoring settings for those APIs. You can have one or multiple projects.

Give your project a name and click **Create**.

![](../../../.gitbook/assets/image%20%2839%29.png)

Once the new project is created you will be able to create your first storage bucket inside this project. In the navigation drawer, click **Storage**.

![](../../../.gitbook/assets/image%20%2834%29.png)

Click **Create bucket**.

![](../../../.gitbook/assets/image%20%2844%29.png)

Specify the bucket name, default storage class, and location. Click **Create**.

![](../../../.gitbook/assets/image%20%2846%29.png)

**Note**: Buckets belong to a particular project and cannot be shared among projects. There is no limit however on the number of buckets that you can create within a project.

## Preparing Service Account

Google Cloud Storage lets you use service accounts to authenticate your application. A service account's credentials include a generated email address that is unique, a client ID, and at least one public/private key pair.

In the navigation drawer, select **API Manager**.

![](../../../.gitbook/assets/image%20%2810%29.png)

Under **Credentials**, expand **Create credentials** and click **Service account key**.

![](../../../.gitbook/assets/image%20%285%29.png)

Specify the service account and the key type \(P12\). Click **Create**.

![](../../../.gitbook/assets/image%20%2823%29.png)

The key will shortly start downloading. The private key's password will be shown on a pop-up window. Write it down somewhere so as to not lose it in the future.

![](../../../.gitbook/assets/image%20%2827%29.png)

In addition to the mentioned file, the service account information will also be displayed in the Credentials Dashboard.

![](../../../.gitbook/assets/image%20%2811%29.png)

You're finished. Now that you've signed up for Google Cloud, it's time to use the newly created credentials when adding a backup destination in MSP Backups.

