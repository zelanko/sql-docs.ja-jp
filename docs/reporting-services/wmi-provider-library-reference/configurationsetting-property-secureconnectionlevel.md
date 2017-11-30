---
title: "SecureConnectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
apiname: SecureConnectionLevel
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
caps.latest.revision: "19"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: be620ce014ce7357a23e20b0cbb61df79775a3b8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-property---secureconnectionlevel"></a>ConfigurationSetting プロパティ - SecureConnectionLevel
  RSReportServer.config ファイルに指定された、セキュリティで保護された接続レベルを返します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>プロパティ値  
 セキュリティで保護された接続レベルを表す **整数** 値。 この戻り値は、SSL が構成されているかどうかを示します。 1 以上の値は、SSL がオンであることを示します。 値 0 は、SSL がオフであることを示します。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
