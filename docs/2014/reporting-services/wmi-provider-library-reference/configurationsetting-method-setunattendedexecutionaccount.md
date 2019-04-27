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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e3c0402d8ae19850c213355cb69cf452e5a3cc0f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62646337"
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
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
