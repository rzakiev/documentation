# Managing Licenses

## Introduction

MSP Backups is distributed on a per-computer basis. In other words, each computer must be assigned a license to be able to perform backups. If a user has multiple computers, each of these computers requires a separate license.

Licenses can be purchased in bulk and thereby shape a global pool or they can be purchased in separate transactions that can be matched with particular companies.

Following is a detailed explanation of how license management works in MSP Backups.

## Purchasing Licenses

To buy licenses, click **Buy Licenses** under _Users, Licenses_ :

![](https://mspbackups.com/contents/images/licenses-buy.png)

Identify the required licenses, specify the number of licenses to be purchased and click **Buy**.

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing1.png)

{% hint style="info" %}
MSP Backups for macOS & Linux requires a _File Backup_ license.
{% endhint %}

Once you've purchased licenses, they will be displayed on the _Licenses_ tab, under _Users_:

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing5.png)

## Allocating Licenses

By default, licenses are automatically allocated to users from the global pool unless you deliberately limit users' available licenses in the users' settings. Namely, when creating or editing a user, you can either authorize the user to request licenses directly from the global pool or allocate them a certain number of available licenses:

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing2.png)

If a user is assigned to a particular company, the user's licensing policy will be overridden by the company's licensing policy:

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing3.png)

Similarly, companies themselves can request licenses from either the global pool or a dedicated company pool. When editing a company's settings, you can select among the following licensing options:

* **Global Pool** \(Default\). With this option selected, paid licenses allocated to new users are obtained from the global \(provider's\) license pool;
* **Company Pool**. This option enables you to grant a specific number of licenses to a company. With this option selected, licenses granted to users of this company are obtained from this company's pool. The total number of licenses granted to all of your companies cannot exceed the total number of licenses available to you in the global pool.
* **Custom.** Selecting this option enables your users to have custom licensing settings specified individually for each user \(as described on the screenshot above\).

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing4.png)

Once the licensing policy is configured for all users and companies, subsequent license allocation will occur automatically according to the policy.

## Releasing Licenses

If a license needs to be released from a computer, simply click _**Release**_ next to the transaction ID:

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing7.png)

In the appeared pop-up window, indicate whether the license should be released and moved back to the user/company pool or moved back to the global license pool:

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/screenshot-2018-06-15-at-17.22.02.png)

## Renewing Licenses

When you purchase a set of licenses for your users in one transaction, all these licenses are automatically renewed every year. And that holds true for all completed transactions. For example, if you purchase 100 licenses for _company A_ on June 1st, 2018, these 100 licenses will automatically be renewed on June 1st, 2019.

Let's suppose auto-renewal failed because your debit card had expired. In this case our service will attempt to renew these 100 licenses from the global license pool. If you don't want our service to renew these licenses from the global pool, go to the Web Console settings and deselect the _Automatic exchange of expired license with available_ checkbox.

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/screenshot-2018-06-25-at-18.17.43.png)

You may want to disable this checkbox to ensure that, for example, licenses from _transaction A_ are exclusively assigned to _company A_ and licenses from other transactions will not be assigned to users of _company A_ because auto-renewal failed for licenses from _transaction A_.

If this checkbox is enabled, failure to renew certain licenses will lead to assignment of other licenses from the global pool to your users.

Expired trial licenses are displayed with a red key on the left and can be renewed by clicking **Grant**.

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/screenshot-2018-06-25-at-18.47.29.png)

## Managing Transactions

When you purchase multiple licenses, all these licenses are automatically assigned to one transaction. Many of our customers prefer to match these transactions with certain companies for more convenient license management. For instance, 10 licenses were purchased in transaction A for company A. If company A requires a few extra licenses, these licenses will have to be purchased in a separate transaction which would make it more difficult to match this company's licenses with a particular transaction.

To deal with this issue, MSP Backups Web Console allows modification of multiple licenses' transaction with the help of a group action. To do that, select the required licenses and click on the key icon in the upper right-hand corner. Click **Change transaction**:

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing9.png)

Select the required transaction and click **Apply**. The licenses will then be assigned to the selected transaction.

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/licensing10.png)

## Licensing Technicalities

While the initial license allocation may seem straightforward at first, it is worth to examine the lifecycle of a license a little further to avoid being caught off guard when performing regular procedures like assigning a user to a different company, deleting user accounts, and so forth.

### Assigning a user to a different company

Assigning a user to a different company may result in moving this user's paid licenses to another pool, which depends on the licensing mode used by both of these companies.

* If the previous company uses the global license pool and the new company uses its own company pool, the user's activated licenses are handed over to the new company's pool and the rest of the user's licenses are moved to the global pool where they become available to users from other companies.
* If the new company uses its own license pool, this user's activated licenses will move to this company's pool. 
* If the new company uses a custom licensing mode, this user's activated licenses will move to the global or user's personal pool, depending on the licensing mode specified for the new company. 
* If the new company uses the global licensing pool, this user's activated licenses will move to the global pool.

### Moving Non-Activated Licenses

If a company enables its users to have personal license pools, a user's pool can contain non-activated licenses. Where these licenses will be moved after assigning a user to a different company depends on the licensing mode specified for the newly assigned company:

* If the new company uses the global licensing pool, a user's non-activated licenses will move to the global pool. 
* If the new company uses its own license pool, a user's non-activated licenses will move to this company's pool. 
* Finally, if the target company uses a custom licensing mode, non-activated licenses will remain in this user's personal pool.

### Deleting a user account

When deleting a user account, this user's licenses will return to either the global or to the company's pool, depending on which pool was used to obtain licenses by this user:

* If the user's licenses were obtained from the global or personal pool, these licenses will return to the global pool. 
* If a user's licenses were obtained from a company's pool, these licenses will return back to the pool of this company.

