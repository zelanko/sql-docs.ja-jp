---
title: "IsSharePointIntegrated プロパティ (WMI) | Microsoft Docs"
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
helpviewer_keywords: IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
caps.latest.revision: "11"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e300196e77e90d245b66707ce69d8b4f4ecf3b49
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-property---issharepointintegrated"></a>ConfigurationSetting プロパティ - IsSharePointIntegrated
  レポート サーバーが SharePoint 統合モードであるかどうかを示します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降、このプロパティは常に **False** を返します。これは、SharePoint モードでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスは SharePoint 共有サービスであり、WMI プロバイダーによって制御されないためです。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>プロパティ値  
 レポート サーバーが SharePoint 統合モードであるかどうかを示す **Boolean** オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
