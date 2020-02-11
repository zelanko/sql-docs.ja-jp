---
title: InitializeReportServer メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5ea9e6e4e36e62828f3036c3765ba42c202448c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098346"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a>InitializeReportServer メソッド (WMI MSReportServer_ConfigurationSetting)
  指定されたレポート サービス インスタンスを初期化します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>パラメーター  
 *InstallationID*  
 暗号化キーを暗号化するための文字列。暗号化キーを返す前に、この文字列を使用して暗号化されます。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
 *ExtendedErrors []*  
 [out] 呼び出しによって返されたその他のエラーを含む文字列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す*HRESULT*を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>解説  
 このメソッドを呼び出すと、レポート サーバー データベースのセキュリティで保護された情報にアクセスする暗号化キーが、 *InstallationID*で特定されるレポート サーバーの公開キーを使用して暗号化されます。  
  
 指定したレポート サーバーの公開キーは、レポート サーバー データベースに書き込んでおく必要があります。  
  
 セキュリティで保護された情報に既にアクセスしたレポート サーバーに対して、 *InitializeReportServer* メソッドを呼び出して、暗号化キーの暗号を解除する必要があります。 次に、暗号化された暗号化キーがレポート サーバー データベースに格納されます。  
  
 [初期化](configurationsetting-property-isinitialized.md)された初期化メソッドが呼び出された`true`ときに、レポートサーバーの isinitialized プロパティがに設定されている場合、メソッドは暗号化キーの暗号化を試行せずに成功を返します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
