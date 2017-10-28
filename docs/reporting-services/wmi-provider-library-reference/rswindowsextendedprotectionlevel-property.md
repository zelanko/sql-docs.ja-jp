---
title: "RSWindowsExtendedProtectionLevel プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9249b6abefe1a36e9b7cdb7aff1213b833113812
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="rswindowsextendedprotectionlevel-property"></a>RSWindowsExtendedProtectionLevel プロパティ
  レポート サーバーがサポートするように構成されている保護のレベルを示す文字列値を返します。 このプロパティは読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>解説  
 レポート サーバーがサポートするように構成されている保護のレベルを示す文字列値を返します。 WMI プロバイダーの接続先のレポート サーバーが拡張保護をサポートしていない場合は、"" (空の文字列) が返されます。 有効な値を次に示します。  
  
 `“Off” | “Allow” | “Require”`  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>参照  
 [RSWindowsExtendedProtectionScenario プロパティ (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [SetExtendedProtectionSettings メソッド & #40 です。WMI MSReportServer_ConfigurationSetting &#41;](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Reporting Services での認証の拡張保護](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  

