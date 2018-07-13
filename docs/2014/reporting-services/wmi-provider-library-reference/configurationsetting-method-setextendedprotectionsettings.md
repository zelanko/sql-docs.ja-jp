---
title: SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fbc49b6978c9d60344795b3c05729e14e9fa3838
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181479"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserverconfigurationsetting"></a>SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting)
  SetExtendedProtectionSettings メソッドは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の構成ファイル (RSReportServer.config) で RSWindowsExtendedProtectionLevel プロパティと RSWindowsExtendedProtectionScenario プロパティを設定するために使用します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ExtendedProtectionLevel*  
 RSRreportserver.config ファイルで RSWindowsExtendedProtectionLevel を設定します。 この必須の値では大文字と小文字は区別されません。  
  
 有効な値を次に示します。  
  
 `”Off | Allow | Require”`  
  
 *ExtendedProtectionScenario*  
 RSReportserver.config ファイルで RSWindowsExtendedProtectionScenario を設定します。 この必須の値では大文字と小文字は区別されません。  
  
 有効な値を次に示します。  
  
 `”Any” | “Proxy” | “Direct”`  
  
## <a name="remarks"></a>コメント  
 RSWindowsExtendedProtectionLevel プロパティと RSWindowsExtendedProtectionScenario プロパティは、RSReportServer.config ファイルの AuthenticationTypes に RSWindowNTLM、RSWindowsNegotiate、または RSWindowsKerberos が含まれている場合に適用されます。 これらのプロパティの設定は、レポート サーバーでのユーザーとクライアント ソフトウェアの認証方法に影響します。 ExtendedProtectionLevel をいずれかに設定する前に、拡張保護のドキュメントを読むことをお勧め`Allow`または`Require`します。  
  
 ExtendedProtectionLevel を設定するには、ユーザーはレポート サーバーの BUILTIN\Administrators グループのメンバーである必要があります。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [RSWindowsExtendedProtectionScenario プロパティ&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [RSWindowsExtendedProtectionLevel プロパティ&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Reporting Services での認証の拡張保護](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md)  
  
  
