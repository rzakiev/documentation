# Creating Users

_User_ is an entity of MSP Backups that corresponds with your end users. Each user may use the same credentials on multiple computers; however, each computer requires a separate license.

To start using MSP Backup on Windows, macOS, or Linux, you need to first create a user and then enter their credentials on the authentication start-up screen.

### Creating a User

To create a user, go to _Users_, under _Users_. Click **Create User**.

![](../../.gitbook/assets/screenshot-2018-06-19-at-18.25.59%20%281%29.png)

Now specify the user's information along with their backup storage:

* **First Name**
* **Last Name**
* **User account**. This will be used when authenticating in the app on the user's computers. It's preferable to use an email address to make it easier to work with the account.
* **Initial password**
* **Notification email**. If you haven't configured the default notification address or would like to specify additional email addresses for notifications, specify them in this text field. Each email address must be separated by a semicolon.
* **Company \(optional\)**. Specify the company to which the user should be assigned. If there are currently no companies available, read the following article that explains in detail how to create a company. It's also possible to just leave this drop-down empty.
* **Account**. This is the cloud or local backup storage that will be used to store the user's backups.
* **Bucket**. Bucket or container of the cloud storage.
* **Storage Limit**. Storage limits restrict the volume of data the user can store in the backup storage. Refer to this article if you haven't configured any storage limits. 
* **User enabled**. Leave this checkbox selected unless the user definitely needs to be disabled for some reason. 
* **Send email with instructions to the user**. If this option is selected, the user will receive an email with the link to the specified builds and instructions on how to get started with the app. The text of the email can be configured in _Emails Customization_, under _Reporting_.
* **Licenses**. Here you can either authorize the user to request licenses directly from the global license pool or restrict them to the specified licenses. Read this article to learn more about license management.

![](../../.gitbook/assets/screenshot-2018-06-19-at-18.40.42.png)

Click **Save** and the user will be created. When done, launch MSP Backups on the user's computer and enter these credentials.

![](../../.gitbook/assets/capture%20%282%29.PNG)



