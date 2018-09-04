---
title: RSWindowsExtendedProtectionScenario プロパティ | Microsoft Docs
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: aa66222fd6880d9559cdae450a07c53a73c2ccab
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2018
ms.locfileid: "43264884"
---
# <a name="rswindowsextendedprotectionscenario-property"></a>RSWindowsExtendedProtectionScenario プロパティ
  レポート サーバーが許可するように構成されている拡張保護のシナリオを示す文字列値を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Remarks  
 レポート サーバーが許可するように構成されている拡張保護のシナリオを示す文字列値を返します。 WMI プロバイダーの接続先のレポート サーバーが拡張保護をサポートしていない場合は、"" (空の文字列) が返されます。  
  
 有効な値を次に示します。  
  
 `”Any | Proxy | Direct”`  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>参照  
 [RSWindowsExtendedProtectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Reporting Services での認証の拡張保護](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
