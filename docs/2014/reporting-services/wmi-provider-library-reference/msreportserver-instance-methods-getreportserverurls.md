---
title: GetReportServerUrls メソッド (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 148e0ece44e97bd4c559bbed9cc95aa97092dffb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171052"
---
# <a name="getreportserverurls-method-wmi-msreportserverinstance"></a>GetReportServerUrls メソッド (WMI MSReportServer_Instance)
  ユーザーがレポート サーバーおよびレポート マネージャーへのアクセスに使用できる URL の一覧を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ApplicationName[]*  
 インストールされているアプリケーションを含む配列。 値は`ReportServerWebService`または`ReportManager`します。  
  
 *URLs[]*  
 正常に登録された URL を含む配列。  
  
 *Length*  
 返された配列の長さを含む整数値。  
  
 *HRESULT*  
 成功を表す値またはエラー コード。  
  
## <a name="return-values"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 WMI 管理オブジェクトによって公開されるメソッドは、InvokeMethod 関数によって呼び出されます。 詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI ドキュメントの「管理オブジェクトのメソッドの実行」を参照してください。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
