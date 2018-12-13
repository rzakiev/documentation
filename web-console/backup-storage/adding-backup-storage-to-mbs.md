# Adding Backup Storage to MSP Backups

### Adding a Cloud Storage

To add a cloud backup storage in MSP Backups, do the following:

1. Under _Storage_, click **Storage Accounts**.

![](../../.gitbook/assets/screenshot-2018-06-20-at-16.33.48.png)

2. Click **Add Account**.

![](../../.gitbook/assets/screenshot-2018-06-20-at-16.34.59.png)

3. Click the required cloud storage, enter your cloud storage credentials and click **Save**.  

![](../../.gitbook/assets/screenshot-2018-06-20-at-16.40.21.png)

#### Adding an Amazon S3 account

If the cloud storage of choice is Amazon S3, specify the following parameters when adding a backup storage:

1. **Display name**. The name of the storage that will be listed in the _Storage Accounts_ tab. Your users will not see this name.
2. **Authentication Type**. Specify the required authentication type. There are three options to choose from:
   * IAM Role \(MBS Wizard\). This is the preferred authentication method. Our service will automatically generate an IAM role with the minimum required permissions in order to operate.
   * IAM Role \(Manual\). This option is aimed at professionals who can manually create an IAM Role in the AWS Console with the required parameters. Once the role is created, specify the Role ARN in the required text field. 

   3. **Access / Secret key**. As per Amazon's recommendations, it's preferable to use IAM roles instead of secret and access keys in order to maximize security. 

   4. **Buckets**. Indicate if you want to use all of your buckets or only specific ones.

![](../../.gitbook/assets/screenshot-2018-06-20-at-16.55.01.png)

{% hint style="info" %}
When authenticating via IAM Role \(MBS Wizard\), MSP Backups uses your access / secret keys only **once** to generate an IAM role. We do not store your keys.
{% endhint %}

#### Adding a Google Cloud account

If the cloud storage of choice is Google Cloud, specify the following parameters when adding a backup storage:

1. **Display name**. The name of the storage that will be listed in the _Storage Accounts_ tab. Your users will not see this name.
2. **Service Account Email**
3. **Binary key**
4. **Project ID**

![](../../.gitbook/assets/screenshot-2018-06-20-at-18.12.13.png)

#### Adding an Azure account

MSP Backups differentiates between Microsoft Azure for backup storage and Microsoft Azure for virtual machines. Configure your account depending on the required functionality. If both backup storage and Azure VM are needed, add two separate accounts. Ensure that both accounts are named properly so that backups to Azure and virtual machine restores to Azure VM are performed smoothly.

Adding an Azure account for storage only requires the display name, account name, and shared key:

![](../../.gitbook/assets/screenshot-2018-06-20-at-18.34.30.png)

Adding an Azure account for VM purposes requires to sign into your Azure VM account. Enter the required display name, click **Sign in** and MSP Backups will do the rest.

![](../../.gitbook/assets/screenshot-2018-06-20-at-18.40.22.png)

### Adding a Local Storage

To add a local storage, select _File System_ when adding a backup storage.

Specify the display name, the local storage path, and click **Save**.

![](../../.gitbook/assets/screenshot-2018-06-20-at-18.50.14.png)

When adding a network share, MSP Backup enables you to specify the login and password:

![](../../.gitbook/assets/screenshot-2018-06-20-at-18.50.39.png)



