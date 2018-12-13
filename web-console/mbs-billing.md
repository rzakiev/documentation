# MBS Billing

### Introduction

The MBS billing system represents a two-component structure that enables providers to charge their customers based on either **storage limits** and/or **storage cost**. The storage limit component allows providers to set custom storage limits for a particular user with a fixed cost while the storage costs component allows users to perform unlimited backup on the pay-as-you-go basis at a pre-defined price \(storage provider's cost + your premium\).

This article explains how to configure storage limits and storage costs and also demonstrates how to view and analyze the billing page of the MBS Web Console.

### Setting Storage Limits

**Storage limits** — also known as **packages** —  enable you to configure a custom storage limit for a particular  or user. This means you can explicitly define the storage space available to a particular user and also how much they must pay for it. For example, you can create a 1-terabyte storage limit priced at $30 dollars and then assign it to a certain user. Even if that user's backup volume is only 600GB, they will still be charged $30 \( and not $30 \* 0.6\). This approach is preferable if you expect each user to bring you at least the specified sum each billing period.

Let's consider a use-case scenario. Suppose you have a user called Charlie with a 100-gigabyte limit for which he pays $5/month, and three other users with a 1-terabyte limit for which they pay $50/month each. In total, these four users will be charged $50 \* 3 + $5 = $155/month. If they exceed the storage limit, their backups will stop and you will have to either increase their storage limit or ask them to reduce their backup volume.

While the storage cost can be configured only for individual users, the storage limit can also be configured for individual companies. But please note that if all users within the company collectively have a storage limit that exceeds the storage limit of the company, their backups will stop executing once they collectively exceed company storage limit. For example, five users with a 1-terabyte storage limit each within a company with a 4-terabyte limit, will be unable to perform backup once they collectively hit the 4-terabyte mark \(even though they have 5 terabytes in total\). Therefore, you're advised to ensure that the company's storage limit is higher than the collective limit of all its users; otherwise, there will be a conflict between the company's and the individual storage limits.

Storage limits can be set on the **Storage Limits** page, under **Storage**. To add a new storage limit, click **Add New**.

![](../.gitbook/assets/storagelimit1.png)

Specify the name of the storage limit and its description. Then specify the number of gigabytes available to users with this storage limit. Next, specify the restore limit and the cost of the storage limit \(charged every month\). You can also optionally specify the preferred Glacier restore type. Click **Save**.

![](../.gitbook/assets/storagelimit2.png)

The storage limit has been created and from now it can be assigned to all new users:

![](../.gitbook/assets/storagelimit3.png)

### Storage Cost

Unlike storage limits that provide fixed storage space at a fixed price, **storage cost**-based billing operates on a pay-as-you-go basis and allows your users to back up an unlimited amount of data at the price at a pre-defined price \(storage provider's cost + your premium\). For example, the standard S3 storage costs $0.023 per GB-month; you can sell it for $0.03 per GB-month with $0.07 being your margin. That way each user does not require a separate storage limit and they can backup any data volume they need. 

For example, suppose you have 50 users who collectively back up 50 terabytes per month. For this volume, you will charge your customers $0.03 \* 50'000 = $**1500**, of which $0.023 \* 50'000 = $**1150** will go to Amazon and the remaining $1500-$1150 = $**350** is your **monthly** **net profit**.

Storage cost for each cloud storage can be configured on the **Storage Accounts** page, under **Storage**. Click on the little gear icon on the right of the required storage, and click **Storage Cost Settings**.

![](../.gitbook/assets/storagelimit4.png)

Here you can specify the backup and restore cost \(Amazon's or other cloud storage provider's price\) as well as the final price for the user \(including your premium\). You can also create a custom storage cost for a particular company or a particular user by clicking **Add Custom Price By Company** or **Add Custom Price By User**.

### Combining Storage Limits and Storage Cost

As a matter of fact, you can combine storage limits and storage costs to be able to charge your users both the basic fee \(storage limit\) and the storage fee based on their backup volume \(storage cost\). For example, let's say you have a user with a 1-terabyte limit for which they pay $30/month. This user backs up monthly 600GB of data to Amazon S3 which you've priced at $0.03 per GB-month. That way the user will pay $30 + $0.03 \* 600 = $**48** every month. 

### Monitoring Billing

The amount of money payable by each customer can be monitored and analyzed on the **Billing** page, under **Reporting**.

This page displays the following information:

1. **Total Limits Cost**. This figure represents the collective cost of all storage limits assigned to your users.
2. **Total due to storage**. This figure represents the collective storage cost \(storage cost for each cloud storage multiplied by the corresponding average space volume\). This is what you pay to Amazon or other storage provider for all the storage space occupied by your users. The difference between the first and the second figure is **your net profit** for the billing period.
3. **Total Cost**. This figure includes all payable sums for this user, including the store cost, storage limit cost, and restore cost. 
4. **Cost Details**. This figure breaks down the third figure \(Total Cost\) into the storage limit cost and the storage cost.

![](../.gitbook/assets/storagelimit6%20%281%29.png)

To view the billing details for a particular user, click **Details**. This page displays the following information:

1. **Total due to storage**. This figure represents the sum you pay to the storage provider like Amazon for this user's storage. 
2. **Net profit**. This figure represents the difference between what you charge this customer and the first figure.

![](../.gitbook/assets/storagelimit7.png)

The sum of these two figures is equal to **Total Cost** from the previous page.









