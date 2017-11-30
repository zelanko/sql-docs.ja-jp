---
title: "SetServiceState メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname: SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
caps.latest.revision: "20"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 85e26f683c03e9b411ae3dc7d17f1b326981740d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-method---setservicestate"></a>ConfigurationSetting メソッド - SetServiceState
  レポート サーバーの Windows サービスおよび Web サービスを開始または停止します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetServiceState(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *EnableWindowsService*  
 Windows サービスの状態を示す **Boolean** 値。 値が **true** の場合はレポート サーバー Windows サービスを開始し、 **false** の場合はレポート サーバー Windows サービスを停止します。  
  
 *EnableWebService*  
 **Web サービスの状態を示す** Boolean [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 値。 値が **true** の場合はレポート サーバー Web サービスを開始し、 **false** の場合はレポート サーバー Web サービスを停止します。  
  
 *EnableReportManager*  
 レポート マネージャーの目的の状態を示す **Boolean** 値。
 
 > [!NOTE] 
 > この設定は、SQL Server 2016 Reporting Services 累積更新プログラム 2 の時点で廃止されました。 Web ポータルは常に有効になります。 値は無視されます。
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
