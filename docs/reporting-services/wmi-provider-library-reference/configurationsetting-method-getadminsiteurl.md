---
title: GetAdminSiteUrl メソッド (WMI) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 40f62a917762d4942cad60dd27ab6db757b42d7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772220"
---
# <a name="configurationsetting-method---getadminsiteurl"></a>ConfigurationSetting メソッド - GetAdminSiteUrl
  レポート サーバーが統合されている Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ファームのサーバー管理 Web サイトの絶対 URL を取得します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *AdminSiteUrl*  
 [out] レポート サーバーが統合されている SharePoint ファームのサーバー管理 Web サイトの絶対 URL を表す文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メソッド](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-methods.md)  
  
  
