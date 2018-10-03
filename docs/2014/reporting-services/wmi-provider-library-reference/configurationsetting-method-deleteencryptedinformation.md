---
title: DeleteEncryptedInformation メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1d6e9ed6c7aa3cf1ac103c157f0084c4c6863167
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081452"
---
# <a name="deleteencryptedinformation-method-wmi-msreportserverconfigurationsetting"></a>DeleteEncryptedInformation メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバー データベースから暗号化された情報を削除します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>パラメーター  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
 *ExtendedErrors[]*  
 [out] 呼び出しによって返されたその他のエラーを含む文字列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを呼び出すと、次のデータが削除されます。  
  
-   ユーザー名とパスワードを含む、暗号化されたデータ ソース情報  
  
-   配信拡張機能インターフェイスを使用して暗号化されたサブスクリプション データ  
  
-   レポート サーバー データベースのキー テーブルからのすべての情報  
  
 このメソッドを呼び出した後は、ユーザーがレポート サーバー データベースを使用する各コンピューターを初期化する必要があります。  
  
 DeleteEncryptedInformation メソッドを呼び出しても、レポート サーバー構成ファイルには影響しません。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
