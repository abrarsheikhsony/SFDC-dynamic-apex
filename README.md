# Salesforce Dynamic Apex

Here you will find information related to dynamic Apex DML, dynamic SOSL, dynamic SOQL, Describe calls, Schema calls etc.

(1) Get the SObject API Name
```
sObject sObjectRecord = new Account();
String objectType = sObjectRecord.getSObjectType().getDescribe().getName();
System.Debug('Object Type / API Name = '+objectType);
//Returns: Object Type / API Name = Account
```

(2) Get the keyprefix or first 3 digits of SObject
```
String keyPrefixAccount = Schema.SObjectType.Account.getKeyPrefix(); 
System.Debug('keyPrefixAccount = '+keyPrefixAccount);
// Returns: keyPrefixAccount = 001
```
