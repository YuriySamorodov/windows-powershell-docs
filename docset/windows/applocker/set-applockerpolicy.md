---
ms.mktglfcycl: manage
ms.sitesec: library
ms.author: kenwith
author: kenwith
description: Use this topic to help manage Windows and Windows Server technologies with Windows PowerShell.
external help file: Microsoft.Security.ApplicationId.PolicyManagement.Cmdlets.dll-Help.xml
keywords: powershell, cmdlet
manager: jasgro
ms.date: 12/20/2016
ms.prod: w10
ms.technology: powershell-windows
ms.topic: reference
online version: 
schema: 2.0.0
title: Set-AppLockerPolicy
ms.reviewer:
ms.assetid: A5B91C2A-73C3-417C-84B1-D430B42860A3
---

# Set-AppLockerPolicy

## SYNOPSIS
Sets the AppLocker policy for the specified GPO.

## SYNTAX

### ByXmlPolicy (Default)
```
Set-AppLockerPolicy [-XmlPolicy] <String> [-Ldap <String>] [-Merge] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByPolicyObject
```
Set-AppLockerPolicy [-PolicyObject] <AppLockerPolicy> [-Ldap <String>] [-Merge] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Set-AppLockerPolicy cmdlet** sets the specified GPO to contain the specified AppLocker policy.
If no Lightweight Directory Access Protocol (LDAP) is specified, then the default is the local GPO.

The input values for the AppLocker policy can be an **AppLockerPolicy** object or an XML-formatted file that contains the AppLocker policy.

## EXAMPLES

### Example 1: Set the local AppLocker policy
```
PS C:\> Set-AppLockerPolicy -XMLPolicy C:\Policy.xml
```

This example sets the local AppLocker policy to the policy specified in C:\Policy.xml.

### Example 2: Set the GPO to contain an AppLocker policy.
```
PS C:\> Set-AppLockerPolicy -XMLPolicy C:\Policy.xml -LDAP "LDAP://DC13.Contoso.com/CN={31B2F340-016D-11D2-945F-00C04FB984F9},CN=Policies,CN=System,DC=Contoso,DC=com"
```

This example sets the GPO specified in the LDAP path to contain the AppLocker policy that is specified in C:\Policy.xml.

### Example 3: Merge the local AppLocker policy with another
```
PS C:\> Get-AppLockerPolicy -Local | Set-AppLockerPolicy -LDAP "LDAP://DC13.Contoso.com/CN={31B2F340-016D-11D2-945F-00C04FB984F9},CN=Policies,CN=System,DC=Contoso,DC=com" -Merge
```

This example gets the local AppLocker policy, and then merges the policy with the existing AppLocker policy in the GPO specified in the LDAP path.
For more information on how two policies are merged, see the *Merge* parameter description.

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ldap
Specifies the LDAP path of the GPO.
It must specify a unique GPO.
If this parameter is not specified, then the local AppLocker policy is set.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Merge
Merges the rules in the specified AppLocker policy with the AppLocker rules in the target GPO specified in the LDAP path.
The merging of policies will remove rules with duplicate rule IDs, and the enforcement setting specified by the AppLocker policy in the target GPO will be preserved.
If the *Merge* parameter is not specified, then the new policy will overwrite the existing policy.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PolicyObject
Specifies the **AppLockerPolicy** object that contains the AppLocker policy.
Can be obtained from the Get-AppLockerPolicy and the New-AppLockerPolicy cmdlets.

```yaml
Type: AppLockerPolicy
Parameter Sets: ByPolicyObject
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs. The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -XmlPolicy
Specifies the path where the XML-formatted file that contains the AppLocker policy is saved.

```yaml
Type: String
Parameter Sets: ByXmlPolicy
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Security.ApplicationId.PolicyManagement.PolicyModel.AppLockerPolicy
**AppLockerPolicy**

### System.String

## OUTPUTS

### None

## NOTES

## RELATED LINKS

[Get-AppLockerFileInformation](./Get-AppLockerFileInformation.md)

[Get-AppLockerPolicy](./Get-AppLockerPolicy.md)

[New-AppLockerPolicy](./New-AppLockerPolicy.md)

[Test-AppLockerPolicy](./Test-AppLockerPolicy.md)

