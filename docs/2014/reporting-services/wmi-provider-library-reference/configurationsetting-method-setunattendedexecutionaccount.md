---
title: SetUnattendedExecutionAccount メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 159bd5e43a9079fe431d921f8275da7a721b5392
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181692"
---
# <a name="setunattendedexecutionaccount-method-wmi-msreportserverconfigurationsetting"></a>SetUnattendedExecutionAccount メソッド (WMI MSReportServer_ConfigurationSetting)
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
  
## <a name="remarks"></a>コメント  
 SetUnattendedExecutionAccount メソッドは、レポート サーバーが指定されたユーザーとしてログインできるかどうかを検証しません。  
  
 SetUnattendedExecutionAccount メソッドを使用してレポート サーバー Windows サービスのコンテキストで自動実行を行うことはできません。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
