---
title: GetReportServerUrls メソッド (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/09/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fb88837f3c9393c561e65c13656bb0e87a516325
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="msreportserverinstance-methods---getreportserverurls"></a>MSReportServer_Instance メソッド - GetReportServerUrls
  ユーザーがレポート サーバーと [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]へのアクセスに使用できる URL の一覧を返します。  
  
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
 インストールされているアプリケーションを含む配列。 値は **ReportServerWebService** または **ReportServerWebApp**です。  
  
 *URLs[]*  
 正常に登録された URL を含む配列。  
  
 *Length*  
 返された配列の長さを含む整数値。  
  
 *HRESULT*  
 成功を表す値またはエラー コード。  
  
## <a name="return-values"></a>戻り値  
  
## <a name="remarks"></a>Remarks  
 WMI 管理オブジェクトによって公開されるメソッドは、InvokeMethod 関数によって呼び出されます。 詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI ドキュメントの「管理オブジェクトのメソッドの実行」を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
