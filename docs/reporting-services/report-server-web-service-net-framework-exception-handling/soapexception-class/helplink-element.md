---
title: "HelpLink 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- HelpLink element
- SoapException class
ms.assetid: a4489103-a874-44c2-8f75-95cb238928ed
caps.latest.revision: 30
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: eaf3c480eb8c0886facc7127406fa0b5a2447b25
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="helplink-element"></a>HelpLink 要素
  **HelpLink**の要素、**詳細**プロパティは、レポート サーバーによって生成される URL 文字列。 この URL は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ヘルプとサポートで管理されている Web ページを指し、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] で発生する特定のエラーに関するヘルプとサポート技術情報の記事を提供します。 URL の構文は、次のようになっています。  
  
 **http://**www.microsoft.com**/**products**/**ee**/**transform.aspx**?EvtSrc**=v*alue***&EvtID**=*value***&ProdName**=*value***&ProdVer**=*value*  
  
 次の表の引数、 **HelpLink** URL。  
  
|引数|値|  
|--------------|-----------|  
|**EvtSrc**|"Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings"|  
|**EvtID**|レポート サーバー エラー コード。たとえば、rsReservedItem。|  
|**ProdName**|"Microsoft SQL%20Server%20Reporting%20Services"。 製品名の値は URL エンコードされています。|  
|**ProdVer**|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のバージョン番号。 「8.00」の値を示します[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]です。|  
  
 次の例を示しています、 **HelpLink**エラー コードに返される URL **rsReservedItem**です。 このエラーは、ユーザーが [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の予約アイテムの変更または削除を試みたときに発生します。  
  
```  
http://www.microsoft.com/products/ee/transform.aspx?  
EvtSrc=Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings  
&EvtID=rsReservedItem&ProdName=Microsoft%20SQL%20Server%20Reporting%20Services&ProdVer=8.00  
```  
  
 アクセスすることができます、 **HelpLink**を使用して、コード内の要素、 **SoapException**クラスです。  
  
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
 [Reporting Services での例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Detail プロパティを使用して、特定のエラーを処理するには](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
