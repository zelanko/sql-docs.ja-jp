---
title: SetWindowsServiceIdentity メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
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
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fc3dfeafab01480fde7eb195363f46946de30ddd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164002"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserverconfigurationsetting"></a>SetWindowsServiceIdentity メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバーの Windows サービスを指定された Windows ユーザーとして実行させ、レポート サーバーを運用できるファイル システム権限をこのアカウントに与えます。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *UseBuiltInAccount*  
 指定したアカウントが組み込み Windows アカウントであるかどうかを示します。  
  
 *アカウント*  
 Windows サービスの実行に使用する "DOMAIN\alias" 形式の Windows アカウント。  
  
 *Password*  
 アカウントのパスワード。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>コメント  
 ときに、 *UseBuiltInAccount*にパラメーターが設定されている`true`Microsoft にレポート サーバーが実行されていると[!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]または Windows XP の値、*名前*、*ドメイン*、および*パスワード*パラメーターは無視され、ローカル システム アカウントを使用します。  
  
 ときに、 *UseBuiltInAccount*にパラメーターが設定されている`true`、レポート サーバーが Windows Server 2003 で実行されていると、*ドメイン*と*パスワード*プロパティは、無視し、[名前] フィールドは、"Builtin\NetworkService"または"builtin \system"または"builtin \localservice"のいずれかを含める必要があります。  
  
 SetWindowsServiceIdentity メソッドはレポート サーバーのインストール ディレクトリのファイルおよびフォルダーに対するファイル権限を設定します。  
  
 指定されたアカウント、*アカウント*パラメーターを必要と`LogonAsService`Windows での権限です。 このメソッドは、指定されたアカウントにこの権限を与えます。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  