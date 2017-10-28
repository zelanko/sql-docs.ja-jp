---
title: "SetWindowsServiceIdentity メソッド (WMI MSReportServer_ConfigurationSetting) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 935e2d44cbfd0363832eb6401b63d4a0b36623b4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setwindowsserviceidentity"></a>SetWindowsServiceIdentity ConfigurationSetting メソッド
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
  
## <a name="remarks"></a>解説  
 *UseBuiltInAccount* パラメーターを **true** に設定しており、レポート サーバーが Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] または Windows XP で実行されている場合、 *Name*、 *Domain*、および *Password* の各パラメーターの値は無視され、ローカル システム アカウントが使用されます。  
  
 *UseBuiltInAccount* パラメーターを **true** に設定しており、レポート サーバーが Windows Server 2003 で実行されている場合、 *Domain* および *Password* プロパティは無視され、名前フィールドには "Builtin\NetworkService"、"Builtin\System"、または "Builtin\LocalService" を指定する必要があります。  
  
 SetWindowsServiceIdentity メソッドはレポート サーバーのインストール ディレクトリのファイルおよびフォルダーに対するファイル権限を設定します。  
  
 *Account* パラメーターに指定するアカウントには Windows の **LogonAsService** 権限が必要です。 このメソッドは、指定されたアカウントにこの権限を与えます。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  

