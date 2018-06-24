---
title: RSWindowsExtendedProtectionScenario プロパティ (WMI MSReportServer_ConfigurationSetting) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: f6fa7fa258d4638f6dbe7d6626e067b95882a779
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073898"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserverconfigurationsetting"></a>RSWindowsExtendedProtectionScenario プロパティ (WMI MSReportServer_ConfigurationSetting)
  レポート サーバーが許可するように構成されている拡張保護のシナリオを示す文字列値を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>コメント  
 レポート サーバーが許可するように構成されている拡張保護のシナリオを示す文字列値を返します。 WMI プロバイダーの接続先のレポート サーバーが拡張保護をサポートしていない場合は、"" (空の文字列) が返されます。  
  
 有効な値を次に示します。  
  
 `”Any | Proxy | Direct”`  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>参照  
 [RSWindowsExtendedProtectionLevel プロパティ&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md)   
 [Reporting Services での認証の拡張保護](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md)  
  
  