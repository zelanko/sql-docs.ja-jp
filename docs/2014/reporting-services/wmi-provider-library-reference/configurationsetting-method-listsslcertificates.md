---
title: ListSSLCertificates メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c2bacf89f7660ca7bc79387d85836352d37141ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238272"
---
# <a name="listsslcertificates-method-wmi-msreportserverconfigurationsetting"></a>ListSSLCertificates メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバー コンピューター上にある証明書の一覧を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *CertificateHash[]*  
 [out] 証明書ハッシュ。  
  
 *CertName[]*  
 [out] 証明書の名前。  
  
 *HostName[]*  
 [out] 証明書のホスト名。  
  
 *Length*  
 [out] *CertificateHash*配列、 *CertName* 配列、および *HostName* 配列の長さを表します。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
