# Salesforce Dynamic Apex

Here you will find information related to dynamic Apex DML, dynamic SOSL, dynamic SOQL, Describe calls, Schema calls etc.

(1)
```
sObject sObjectRecord = new Account();
String objectType = sObjectRecord.getSObjectType().getDescribe().getName();
System.Debug('Object Type / API Name =:'+objectType);
Object Type / API Name =: Account
```
