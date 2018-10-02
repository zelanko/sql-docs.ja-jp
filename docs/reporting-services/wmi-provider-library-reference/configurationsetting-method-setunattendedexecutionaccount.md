---
title: SetUnattendedExecutionAccount メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 85a3eac1ce8b8b390f186827451b12558abae11b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47738900"
---
# <a name="configurationsetting-method---setunattendedexecutionaccount"></a>ConfigurationSetting メソッド - SetUnattendedExecutionAccount
  レポートの自動実行に使用するアカウントを指定します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *UserName*  
 自動実行で使用する Windows アカウント。  
  
 *Password*  
 指定したアカウントのパスワード。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
 SetUnattendedExecutionAccount メソッドは、レポート サーバーが指定されたユーザーとしてログインできるかどうかを検証しません。  
  
 SetUnattendedExecutionAccount メソッドを使用してレポート サーバー Windows サービスのコンテキストで自動実行を行うことはできません。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
