---
title: RemoveSSLCertificateBindings メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveSSLCertificateBindings method
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c923e2c92e22080f2b640afcec83c147ba3cfb6a
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59951038"
---
# <a name="removesslcertificatebindings-method-wmi-msreportserverconfigurationsetting"></a>RemoveSSLCertificateBindings メソッド (WMI MSReportServer_ConfigurationSetting)
  SSL 証明書のバインドを削除します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub RemoveSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveSSLCertificateBindings(string Application,  
    string CertificateHash, string IPAddress, Int32 Port, Int32 Lcid,  
    out string Error, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *アプリケーション*  
 証明書のバインドを削除する必要のあるアプリケーションの名前。  
  
 *CertificateHash*  
 証明書のハッシュ。  
  
 *IPAddress*  
 アプリケーションの IP アドレス。  
  
 *ポート*  
 バインドに関連付けられた SSL ポート。  
  
 *lcid*  
 返されるエラー メッセージに使用するロケール。  
  
 *Error*  
 [out] 発生したエラーの説明。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、rsreportserver.config ファイルおよび HTTP.SYS (オプション) から特定のバインドを削除します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
