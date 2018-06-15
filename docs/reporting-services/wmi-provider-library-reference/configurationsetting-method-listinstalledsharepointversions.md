---
title: ListInstalledSharePointVersions メソッド (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a9b1f06ac8be8563fd19520896e022a4adc4d936
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031609"
---
# <a name="configurationsetting-method---listinstalledsharepointversions"></a>ConfigurationSetting メソッド - ListInstalledSharePointVersions
  レポート サーバーと同じコンピューターにインストールされた Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] のバージョンを表すトークンのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *VersionTokens[]*  
 [out] インストールされたレポート サーバーと互換性がある SharePoint 製品またはテクノロジのバージョンを表すトークンを含む配列。  
  
 *[データ型]*  
 [out] バージョン トークンの配列の長さ。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
 返される各トークンは、現在インストールされているレポート サーバーと互換性がある [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] または [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] のバージョンを表します。 SharePoint の特定のバージョンに、それよりも前の SharePoint バージョンとの互換性がある場合は、互換性がある各 SharePoint バージョンのトークンが返されます。  
  
 次の表は、返される SharePoint のトークンを示しています。  
  
|**バージョン トークン**|**[説明]**|  
|------------------------|---------------------|  
|WSS_V2_Compatible|[!INCLUDE[winSPServ](../../includes/winspserv-md.md)]2.0 と互換性がある [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 、または [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] がインストールされています。|  
|WSS_V3_Compatible|[!INCLUDE[winSPServ](../../includes/winspserv-md.md)]3.0 と互換性がある [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 、または [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] がインストールされています。|  
|WSS_V4_Compatible|Office 14 と互換性がある [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] がインストールされています。|  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
