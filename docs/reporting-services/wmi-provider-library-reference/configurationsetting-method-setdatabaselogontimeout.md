---
title: SetDatabaseLogonTimeout メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetDatabaseLogonTimeout method
ms.assetid: b8773596-5b98-4355-a4ab-4412e1317c67
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9d29ca6fc243a3c7c626784b8075aa7e856f0403
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="configurationsetting-method---setdatabaselogontimeout"></a>ConfigurationSetting メソッド - SetDatabaseLogonTimeout
  レポート サーバー データベース接続の既定のタイムアウト値を指定します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetDatabaseLogonTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseLogonTimeout(Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *LogonTimeout*  
 レポート サーバー データベース接続に関する秒単位の既定のタイムアウト値。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
