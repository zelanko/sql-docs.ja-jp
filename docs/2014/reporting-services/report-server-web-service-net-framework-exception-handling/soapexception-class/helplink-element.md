---
title: HelpLink 要素 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- HelpLink element
- SoapException class
ms.assetid: a4489103-a874-44c2-8f75-95cb238928ed
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 358c0b03e56130fed642fe1ff0bbbc80f9717170
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041103"
---
# <a name="helplink-element"></a>HelpLink 要素
  **Detail** プロパティの **HelpLink** 要素は、レポート サーバーで生成される URL 文字列です。 この URL は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ヘルプとサポートで管理されている Web ページを指し、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] で発生する特定のエラーに関するヘルプとサポート技術情報の記事を提供します。 URL の構文は、次のようになっています。  
  
 **http://** www.microsoft.com**/** 製品**/** ee**/** transform.aspx**でしょうか。EvtSrc**=_値_**& 情報が必要な**=_値_**& ProdName** =_値_**& ProdVer**=_値_  
  
 次の表は、**HelpLink** URL の引数を示しています。  
  
|引数|値|  
|--------------|-----------|  
|**EvtSrc**|"Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings"|  
|**EvtID**|レポート サーバー エラー コード。たとえば、rsReservedItem。|  
|**ProdName**|"Microsoft SQL%20Server%20Reporting%20Services"。 製品名の値は URL エンコードされています。|  
|**ProdVer**|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のバージョン番号。 "8.00" の値は、[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] を示します。|  
  
 次の例を示しています、 **HelpLink**エラー コードで返される URL`rsReservedItem`します。 このエラーは、ユーザーが [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の予約アイテムの変更または削除を試みたときに発生します。  
  
```  
https://www.microsoft.com/products/ee/transform.aspx?  
EvtSrc=Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings  
&EvtID=rsReservedItem&ProdName=Microsoft%20SQL%20Server%20Reporting%20Services&ProdVer=8.00  
```  
  
 コードで **HelpLink** 要素にアクセスするには、**SoapException** クラスを使用します。  
  
```vb  
Try  
   rs.DeleteItem("/Report1")  
  
Catch e As SoapException  
   Console.WriteLine(e.Detail("HelpLink").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.DeleteItem("/Report1");  
}  
  
catch (SoapException e)  
{  
   Console.WriteLine(e.Detail["HelpLink"].InnerXml);  
}  
```  
  
## <a name="see-also"></a>参照  
 [Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](reporting-services-soapexception-class.md)   
 [Detail プロパティを使用したエラー処理](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
