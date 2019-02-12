---
title: IsSharePointIntegrated プロパティ (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 692cd915c893b9f2f0d2d7d83ce17e41f20d070a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029163"
---
# <a name="issharepointintegrated-property-wmi-msreportserverinstance"></a>IsSharePointIntegrated プロパティ (WMI MSReportServer_Instance)
  レポート サーバーが SharePoint 統合モードであるかどうかを示します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降、このプロパティは常に `False` を返します。これは、SharePoint モードでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスは SharePoint 共有サービスであり、WMI プロバイダーによって制御されないためです。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>プロパティ値  
 レポート サーバーが SharePoint 統合モードであるかどうかを示す `Boolean` 値。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_Instance メンバー](msreportserver-instance-members.md)   
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
  
