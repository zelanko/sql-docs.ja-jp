---
title: "UnattendedExecutionAccount プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "UnattendedExecutionAccount"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "UnattendedExecutionAccount プロパティ"
ms.assetid: ab5203ba-c01e-4020-8619-ee290cf9da07
caps.latest.revision: 17
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# UnattendedExecutionAccount プロパティ (WMI MSReportServer_ConfigurationSetting)
  自動的にレポートを実行する場合に、レポート サーバーが権限を借用するユーザー アカウントを返します。 読み取り専用です。  
  
## 構文  
  
```vb  
Public Dim UnattendedExecutionAccount As String  
```  
  
```csharp  
public string UnattendedExecutionAccount;  
```  
  
## プロパティ値  
 アカウント名を表す **String** オブジェクト。  
  
## コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## 必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## 参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  