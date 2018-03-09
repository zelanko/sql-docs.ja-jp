---
title: "IsSharePointIntegrated プロパティ (WMI MSReportServer_Instance) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: "13"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 67fc8c606dfa194a8b5fe6c7ec3fb647628f0022
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="msreportserverinstance-properties---issharepointintegrated"></a>MSReportServer_Instance プロパティ - IsSharePointIntegrated
  レポート サーバーが SharePoint 統合モードであるかどうかを示します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降、このプロパティは常に **False** を返します。これは、SharePoint モードでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスは SharePoint 共有サービスであり、WMI プロバイダーによって制御されないためです。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>プロパティ値  
 レポート サーバーが SharePoint 統合モードであるかどうかを示す **Boolean** 値。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_Instance メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-members.md)   
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  
