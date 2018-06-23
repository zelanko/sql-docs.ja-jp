---
title: UnattendedExecutionAccount プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- UnattendedExecutionAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- UnattendedExecutionAccount property
ms.assetid: ab5203ba-c01e-4020-8619-ee290cf9da07
caps.latest.revision: 17
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 4f97cc66d94459064cc9e71806641533e9cbc064
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085586"
---
# <a name="unattendedexecutionaccount-property-wmi-msreportserverconfigurationsetting"></a>UnattendedExecutionAccount プロパティ (WMI MSReportServer_ConfigurationSetting)
  自動的にレポートを実行する場合に、レポート サーバーが権限を借用するユーザー アカウントを返します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim UnattendedExecutionAccount As String  
```  
  
```csharp  
public string UnattendedExecutionAccount;  
```  
  
## <a name="property-values"></a>プロパティ値  
 アカウント名を表す `String` オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  