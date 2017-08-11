---
title: "WindowsServiceIdentityConfigured プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- WindowsServiceIdentityConfigured
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- WindowsServiceIdentityConfigured property
ms.assetid: ebf8e559-7fe4-4a01-9810-85f18fc04596
caps.latest.revision: 17
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: cd668d2e660d41d2c2881a5500696a988b9a40b8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="windowsserviceidentityconfigured-property"></a>WindowsServiceIdentityConfigured プロパティ
  レポート サーバー Windows サービスが実行するように最後に構成された ID を返します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim WindowsServiceIdentityConfigured As String  
```  
  
```csharp  
public string WindowsServiceIdentityConfigured;  
```  
  
## <a name="property-values"></a>プロパティ値  
 最後に構成されたレポート サーバー Windows サービスを実行する ID が入った **文字列** 値。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
