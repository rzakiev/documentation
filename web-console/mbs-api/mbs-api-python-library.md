---
description: >-
  This page explains how to use MBS API with the help a dedicated Python
  library.
---

# MBS API Python Library

## Introduction

In the previous articles we covered the ins and outs of each MBS API request. But just to make things simpler, we've created a Python library that provides methods for each API request available. This library will enable you to send MBS API requests with just a single line of code and should facilitate automation of MBS functionality.

The library can be downloaded [here](https://documentationrobert.s3.amazonaws.com/MBSAPIrequests.py).

## Setup & Initial Authentication

```python
from MBSAPI import *

#Create and initialize an MBSRequester object
mbsAPIinstance = MBSRequester(username = 'MBSAPIlogin', password = 'MBSAPIpassword') #these credentials can be generated in MBS Web Console, in settings.
```

## Managing Users

```python
#List existing users
jsonUsers = mbsAPIinstance.listUsers()

#Create a new user
newUser = {
    "Email" : "roberttech3", #required
    "Password" : "splendidpass", #required
    "Enabled" : True #required
}
mbsAPIinstance.createNewUser(newUser)

#Get user's info by ID
mbsAPIinstance.getUserByID('sampleID-898g90sg8d-9sdf9f-sdfsd9')

#Get user's info by login & password
userInfoJSON = mbsAPIinstance.getUserByLoginPassword("roberttech3", "splendidpass")

#Update user's info
updatedUser = {
    "ID" : "9d6de082-741c-44fe-b067-1a36eb03fa40", #required
    "Password" : "newUnhackablePass", #required
    "Enabled" : False #required
}
mbsAPIinstance.updateUserInfo(updatedUser)

#Delete a user while retaining their data
mbsAPIinstance.deleteUserWithoutData("MBSUserID")

#Delete a user and their data
mbsAPIinstance.deleteUserAndData("MBSUserID")

#List a user's computers and backup storage
mbsAPIinstance.listUsersComputersandStorage("MBSuserID")

#Delete a user's data from backup storage
data = {
    "DestinationId": "b17266e7-8b8e-4c3f-b1bb-911b9sdf",
    "ComputerName": "Charlie Marketing MacBook"
}
mbsAPIinstance.deleteUsersData("MBSUserID", data)
```

## Managing Accounts \(Backup Storage\)

```python
#List existing storage accounts
accounts = mbsAPIinstance.getAccounts()

#Get an account's information
accountInfoJSON = mbsAPIinstance.getAccountInfo('accountID')

#Add a new account
newAccount = {
    "DisplayName" : "My S3 account NEW",
    "Type" : 0,
    "AccountSettings" : {
        "AmazonS3": {
            "AccessKey" : "someKeyXPUW2UXRWQYYBYQ",
            "SecretKey" : "someKeyed4kunLB+sxKPaRsEEfQe8J6Y33huFOWcZ4T",
            "IsGovCloud" : False
        }
    }
}
mbsAPIinstance.addAccount(newAccount)

#Edit an existing account
editedAccount = {
    "AccountID" : "MBSAccountID-97f0-4df9-a867-f158ad01220d",
    "DisplayName" : "My S3 account NEW",
    "Type" : 0,
    "AccountSettings" : {
        "AmazonS3": {
            "AccessKey" : "someKeyPUW2UXRWQYYBYQ",
            "SecretKey" : "someKeywed4kunLB+sxKPaRsEEfQe8J6Y33huFOWcZ4T",
            "IsGovCloud" : False
        }
    }
}
mbsAPIinstance.editAccount(editedAccount)

#Add destination to an account
newDestination = {
    "AccountID" : "someID-97f0-4df9-a867-f158ad01220d",
    "Destination" : "s3Bucket",
    "DestinationDisplayName" : "Container for PowerPoints"
}
mbsAPIinstance.addDestination(newDestination)

#Remove a destination from an account
obsoleteDestination = {
    "AccountID" : "someID-97f0-4df9-a867-f158ad01220d",
    "Destination" : "s3Bucket",
    "DestinationDisplayName" : "Container for PowerPoints"
}
mbsAPIinstance.removeDestination(obsoleteDestination)
```

## Managing Destinations

```python
#List existing destinations
mbsAPIinstance.listDestinations()

#List a user's destinations
mbsAPIinstance.listDestinationsForUser("userEmail")

#Add a new destination to a user
s3Destination = {
    "userID" : "someID-f98c-4fbd-aa0d-b1b5551f2df3",
    "AccountID" : "someAccount-dd51-45bf-9e2b-91f0ff9b5e41",
    "Destination" : "s3Bucket",
    "PackageID" : "27755"
}
mbsAPIinstance.addDestinationToUser("userEmail", s3Destination))

#Edit a user's destination
modifiedDestination = {
    "ID" : "destinationID-4b90-46fe-8d98-e0c0327fa794",
    "UserID" : "MBSuserID-f98c-4fbd-aa0d-b1b5551f2df3",
    "AccountID" : "accountID-dd51-45bf-9e2b-91f0ff9b5e41",
    "Destination" : "s3Bucket",
    "PackageID" : "27755"
}
mbsAPIinstance.editDestination(modifiedDestination)

#Delete a user's destination
mbsAPIinstance.deleteDestinationForUser("destinationID", "MBSuserID")
```

## Managing Packages \(Storage Limits\)

```python
#List existing packages
packagesJSON = mbsAPIinstance.listPackages()

#Get a particular package structure
package = mbsAPIinstance.getPackageStructure('packageID')

#List a user's packages:
charliesPackages = mbsAPIinstance.getUsersPackages('MBSuserID')

#Create a new package
newPackage = {
    "Name" : "100-GB Limit",
    "Description" : "Royal Limit",
    "StorageLimit" : 100.0,
    "isGlacierRestoreLimit" : False,
    "GlacierRestoreType" : 0,
    "Cost" : 100.0,
    "UseRestoreLimit" : True
}
mbsAPIinstance.createNewPackage(newPackage)

#Edit an existing package
editedPackage = {
    "ID" : "44988",
    "Enabled" : True,
    "Name" : "100-GB Limit",
    "Description" : "Royal Limit",
    "StorageLimit" : 100.0,
    "isGlacierRestoreLimit" : False,
    "GlacierRestoreType" : 0,
    "Cost" : 75.0,
    "UseRestoreLimit" : True
}
mbsAPIinstance.editPackage(editedPackage)

#Delete a package
mbsAPIinstance.deletePackage('MBSPackageID')
```

## Monitoring

```python
#Get all plans execution history
mbsAPIinstance.monitoring()

#Get plan execution history for a particular user 
mbsAPIinstance.monitoringForuser('MBSuserID')
```

## Managing Licenses

```python
#List available licenses
licenses = mbsAPIinstance.getLicenses()

#Get information on a particular license
licenseInfo = mbsAPIinstance.getLicenseInfo('licenseID')

#Grant a license to a user
mbsAPIinstance.grantLicenseToUser('licenseID', 'userID')

#Release a license from a user
mbsAPIinstance.releaseLicenseFromUser('licenseID', 'userID')

#Revoke a license from a user
mbsAPIinstance.revokeLicenseFromUser('licenseID', 'userID')
```

## Managing Billing

```python
#Get billing information for the current month
billingInfo = mbsAPIinstance.billingDetailsForCurrentMonth()

#Get billing information for a particular company
criteria = {
  "CompanyName": "Los Pollos Hermanos",
  "Date": "2018-05-15T12:38:46.8345309+00:00"
}
billingInfo = mbsAPIinstance.billingDetailsFilteredBy(criteria)

#Get billing information for a particular user
userInfo = {
  "UserID": "userID-96e4-4033-8658-ab1ac6882039",
  "Date": "2018-05-15T12:38:47.3032803+00:00"
}
billingInfo = mbsAPIinstance.billingDetailsForUser(userInfo)
```

## Managing Builds

```python
#List available builds
builds = mbsAPIinstance.getBuilds()

#Request a custom build
requiredBuild = {
  "Editions": [0, 2, 5],
  "Type": 0
}
mbsAPIinstance.requestCustomBuild(requiredBuild)

#List latest versions
latestVersionsJSON = mbsAPIinstance.getLatestVersions()
```

## Managing Administrators

```python
#List existing administrators
administratorsJSON = mbsAPIinstance.listAdministrators()

#Get an administrator's information by ID
adminInfoJSON = mbsAPIinstance.getAdministratorByID('adminID')

#Delete an existing administrator
mbsAPIinstance.deleteAdministrator(adminID)

#Create a new administrator
newAdmin = {
    "Email" : "test@test.com",
    "InitialPassword" : "truepass",
    "SendInstruction" : "true",
    "FirstName" : "Robert",
    "LastName" : "QA",
    "Enabled" : "true",
    "PermissionsModels": {
        "Users": 1,
        "StorageLimit": 1,
        "Notification": 0,
        "OnlineAccess": 1,
        "Licenses": 1,
        "Billing":1,
        "Monitiring":1,
        "RemoteDeploy":1,
        "RemoteManagment":1,
        "HelpMarketing":1,
        "AuditLog":1,
        "PSA":1,
        "Administrators":1,
        "Rebranding":1,
        "Storage":1,
        "ADS":1,
        "LicenseBuy":1,
        "LicenseActivate":1,
        "StorageUsage":1,
        "CapacityReport":1,
        "GoogleApps":1,
        "Dashboard":1
    }
}
mbsAPIinstance.createNewAdministrator(newAdmin)

#Modify an existing administrator
updatedAdmin = {
    "AdminID" : "someID",
    "Password" : "truepass",
    "FirstName" : "Robert",
    "LastName" : "QA",
    "Enabled" : "true",
    "PermissionsModels": {
        "Users": 1,
        "StorageLimit": 1,
        "Notification": 0,
        "OnlineAccess": 1,
        "Licenses": 1,
        "Billing":1,
        "Monitiring":1,
        "RemoteDeploy":1,
        "RemoteManagment":1,
        "HelpMarketing":1,
        "AuditLog":1,
        "PSA":1,
        "Administrators":1,
        "Rebranding":1,
        "Storage":1,
        "ADS":1,
        "LicenseBuy":1,
        "LicenseActivate":1,
        "StorageUsage":1,
        "CapacityReport":1,
        "GoogleApps":1,
        "Dashboard":1
    }
}
mbsAPIinstance.updateAdministrator(updatedAdmin)
```

