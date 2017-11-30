---
title: "UnattendedExecutionAccount プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname: UnattendedExecutionAccount
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: UnattendedExecutionAccount property
ms.assetid: ab5203ba-c01e-4020-8619-ee290cf9da07
caps.latest.revision: "17"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 442a04393fd056f2678b6b39c7acc4cfa1148151
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-property---unattendedexecutionaccount"></a>ConfigurationSetting プロパティ - UnattendedExecutionAccount
  自動的にレポートを実行する場合に、レポート サーバーが権限を借用するユーザー アカウントを返します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim UnattendedExecutionAccount As String  
```  
  
```csharp  
public string UnattendedExecutionAccount;  
```  
  
## <a name="property-values"></a>プロパティ値  
 アカウント名を表す **String** オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
