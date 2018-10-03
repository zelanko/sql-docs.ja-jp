---
title: ListIPAddresses メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3b8dc70cf1502363585abd7f1be5de7c72c6256a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062642"
---
# <a name="listipaddresses-method-wmi-msreportserverconfigurationsetting"></a>ListIPAddresses メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバー コンピューターの IP アドレスを一覧表示します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *IPAddress[]*  
 [out] コンピューターの IP アドレスの一覧。  
  
 *IPVersion[]*  
 [out] IP アドレスのバージョン。  
  
 *IsDhcpEnabled[]*  
 [out] IP アドレスが DHCP 対応かどうか。  
  
 *Length*  
 [out] メソッドによって返される配列の長さ。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。  
  
## <a name="remarks"></a>コメント  
 *IPVersion* の文字列は、"V4" または "V6" です。  
  
 場合*IsDhcpEnabled*は`True`、 *IPAddress*は動的です。 これは、SSL バインドには使用しないでください。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
