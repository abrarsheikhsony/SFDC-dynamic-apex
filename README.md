# Salesforce Dynamic Apex

Here you will find information related to dynamic Apex DML, dynamic SOSL, dynamic SOQL, dynamic strings, Describe calls, Schema calls etc.

(1) Dynamic Strings
```
String customLabel = 'Marc has got {0} marks out of {1}';
List<String> lstCustomLabelIndexStrings = new List<String>{'800', '1000'};
String result = String.format(customLabel, lstCustomLabelIndexStrings);
System.Debug('Returns: '+result);

//Returns: Marc has got 800 marks out of 1000
```

(2) Get the SObject API Name
```
sObject sObjectRecord = new Account();
String objectType = sObjectRecord.getSObjectType().getDescribe().getName();
System.Debug('Object Type / API Name = '+objectType);
//Returns: Object Type / API Name = Account
```

(3) Get the keyprefix or first 3 digits of SObject
```
String keyPrefixAccount = Schema.SObjectType.Account.getKeyPrefix(); 
System.Debug('keyPrefixAccount = '+keyPrefixAccount);
// Returns: keyPrefixAccount = 001
```
(4) Get the RecordType Info by Name or Id

```
Schema.DescribeSObjectResult describeSObjectResult = Account.SobjectType.getDescribe();
Map<String,Schema.RecordTypeInfo> mapRecordTypeInfosByName = describeSObjectResult.getRecordTypeInfosByName();
Map<Id,Schema.RecordTypeInfo> mapRecordTypeInfosById = describeSObjectResult.getRecordTypeInfosById();

System.Debug('Returns: RecordTypeInfosByName '+ mapRecordTypeInfosByName );
System.Debug('Returns: RecordTypeInfosById '+ mapRecordTypeInfosById );
```

```
//Returns: RecordTypeInfosByName

{
Master=Schema.RecordTypeInfo[getName=Master;getRecordTypeId=012000000000000AAA;isActive=true;isAvailable=true;isDefaultRecordTypeMapping=false;isMaster=true;],
Record Type 1=Schema.RecordTypeInfo[getName=Record Type 1;getRecordTypeId=01290000000OUHfAAO;isActive=true;isAvailable=true;isDefaultRecordTypeMapping=true;isMaster=false;],
Record Type 2=Schema.RecordTypeInfo[getName=Record Type 2;getRecordTypeId=01290000000OUHkAAO;isActive=true;isAvailable=true;isDefaultRecordTypeMapping=false;isMaster=false;]
}
```

```
//Returns: RecordTypeInfosById

{
012000000000000AAA=Schema.RecordTypeInfo[getName=Master;getRecordTypeId=012000000000000AAA;isActive=true;isAvailable=true;isDefaultRecordTypeMapping=false;isMaster=true;],
01290000000OUHfAAO=Schema.RecordTypeInfo[getName=Record Type 1;getRecordTypeId=01290000000OUHfAAO;isActive=true;isAvailable=true;isDefaultRecordTypeMapping=true;isMaster=false;],
01290000000OUHkAAO=Schema.RecordTypeInfo[getName=Record Type 2;getRecordTypeId=01290000000OUHkAAO;isActive=true;isAvailable=true;isDefaultRecordTypeMapping=false;isMaster=false;]
}
```
