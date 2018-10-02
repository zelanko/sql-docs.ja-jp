---
title: DeleteEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DeleteEncryptionKey method
ms.assetid: ed2f25b6-6a63-468d-9279-a577ca01b096
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bd67aa73ecb6ccc7bb9496542c818ef558349954
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47630520"
---
# <a name="configurationsetting-method---deleteencryptionkey"></a>ConfigurationSetting メソッド - DeleteEncryptionKey
  レポート サーバー データベースから暗号化キーを削除します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub DeleteEncryptionKeys(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptionKeys(string InstallationID, out Int32 HRESULT,   
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>パラメーター  
 *InstallationID*  
 レポート サーバー データベースのキー テーブルにあるレポート サーバーのインストール ID。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
 *ExtendedErrors[]*  
 [out] 呼び出しによって返されたその他のエラーを含む文字列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す HRESULT を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
 *DeleteEncryptionKey* メソッドは、レポート サーバー データベースのセキュリティで保護された情報にアクセスするレポート サーバーのキー テーブルからエントリを削除します。 指定した *InstallationID* パラメーターがデータベースのインストール ID に対応しない場合、メソッドはエラーを返します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
