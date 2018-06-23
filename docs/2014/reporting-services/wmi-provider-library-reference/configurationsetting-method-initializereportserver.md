---
title: InitializeReportServer メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
caps.latest.revision: 20
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e5c3ace1e9e4cb25fde4d836bc15ad9f30eee3e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084928"
---
# <a name="initializereportserver-method-wmi-msreportserverconfigurationsetting"></a>InitializeReportServer メソッド (WMI MSReportServer_ConfigurationSetting)
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
  
 *ExtendedErrors[]*  
 [out] 呼び出しによって返されたその他のエラーを含む文字列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>コメント  
 このメソッドを呼び出すと、レポート サーバー データベースのセキュリティで保護された情報にアクセスする暗号化キーが、 *InstallationID*で特定されるレポート サーバーの公開キーを使用して暗号化されます。  
  
 指定したレポート サーバーの公開キーは、レポート サーバー データベースに書き込んでおく必要があります。  
  
 セキュリティで保護された情報に既にアクセスしたレポート サーバーに対して、 *InitializeReportServer* メソッドを呼び出して、暗号化キーの暗号を解除する必要があります。 次に、暗号化された暗号化キーがレポート サーバー データベースに格納されます。  
  
 場合、レポート サーバーの[IsInitialized](configurationsetting-property-isinitialized.md)プロパティに設定されている`true`InitializeReportServer メソッドが呼び出されると、メソッドは暗号化キーの暗号化を試みることがなく成功を返します。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  