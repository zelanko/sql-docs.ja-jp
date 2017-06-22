---
title: "プロパティの詳細 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
caps.latest.revision: 33
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f2359ac68758ba2846c4a9065f6cb1c9c96a7e01
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="detail-property"></a>Detail プロパティ
  **詳細**のプロパティ、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException**クラスには、次の XML 構造。  
  
## <a name="elements"></a>要素  
 **詳細**  
 他のすべてのエラー詳細要素を含む最上位要素。  
  
 **ErrorCode**  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 固有のエラー コード。  
  
 **サブコード**  
 HTTP 状態コード。  
  
 **メッセージ**  
 レポート サーバーが割り当てたエラー メッセージとエラー コード。  
  
 **HelpLink**  
 エラーの詳細情報を参照できる Web サイトへのヘルプ リンクの URL。 詳細については、次を参照してください。 [HelpLink 要素](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md)です。  
  
 **LinkID**  
 リンクに割り当てられた ID です。  
  
 **ProductName**  
 製品の名前です。 既定値は**Microsoft SQL Server Reporting Services**です。  
  
 **ProductVersion**  
 バージョン[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]します。 最大長は 15 文字です。 バージョン番号の形式は、8.00.0xxx.00 のようになります。  
  
 **ProductLocaleId**  
 アプリケーションの INTL DLL のロケール ID または言語 ID (0x41A など)。  
  
 **オペレーティング システム**  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] インストール先のオペレーティング システム。 有効な値は**0**独立しており、オペレーティング システムの**1**の[!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)]、および**16** Windows XP 用です。  
  
 **CountryLocaleId**  
 オペレーティング システムのロケール ID または言語 ID。 たとえば、Windows のフランス語バージョンの値は 0x040c です。  
  
 **MoreInformation**  
 メソッド実行中に発生した入れ子にされた例外を含む XML 文字列です。  
  
 **ソース**  
 子要素**MoreInformation**です。 エラーのソースです。  
  
 **メッセージ**  
 子要素**MoreInformation**です。 入れ子にされた例外のエラー メッセージです。 この要素には、XML 属性が含まれています。 **ErrorCode**と**HelpLink**です。  
  
 **Warnings**  
 レポート処理から返された警告を含む XML 文字列です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services での例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Detail プロパティを使用して、特定のエラーを処理するには](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
