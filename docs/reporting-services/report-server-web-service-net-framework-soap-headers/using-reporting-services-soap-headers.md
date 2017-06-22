---
title: "レポートを使用するサービスの SOAP ヘッダー |Microsoft ドキュメント"
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
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
caps.latest.revision: 39
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 79f67a1d6e982aa9b83fcc5bf4c043eb378478d1
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="using-reporting-services-soap-headers"></a>Reporting Services の SOAP ヘッダーの使用
  SOAP を使用した Web サービス メソッドとの通信では、標準形式に従います。 この標準形式の一部は、XML ドキュメントでエンコードされるデータです。 XML ドキュメントは、ルート**エンベロープ**要素、必須の順番で構成される**本文**要素と省略可能な**ヘッダー**要素。 **本文**要素には、メッセージに固有のデータが含まれています。 省略可能な**ヘッダー**要素は、特定のメッセージに直接関連しない追加の情報を含めることができます。 場合は、各子要素、**ヘッダー**要素は、SOAP ヘッダーと呼ばれます。  
  
 SOAP ヘッダーには、メッセージに関連するデータを含めることができますが、一般的には Web サーバー内のインフラストラクチャによって処理される情報が含まれます。  
  
 レポート サーバー Web サービスでは、SOAP ヘッダーで使用される複数のクラス、つまり <xref:ReportService2005.BatchHeader>、<xref:ReportService2010.ItemNamespaceHeader>、<xref:ReportService2010.ServerInfoHeader>、<xref:ReportService2010.TrustedUserHeader>、および <xref:ReportExecution2005.ExecutionHeader> を定義します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[バッチ処理方式](../../reporting-services/report-server-web-service-net-framework-soap-headers/batching-methods.md)|<xref:ReportService2005.BatchHeader> を使用して、複数の操作を 1 つのトランザクションにまとめる方法を説明します。|  
|[実行状態の識別](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)|セッションの状態を管理する方法について説明[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を使用して**SessionHeader**です。|  
|[GetProperties メソッドの項目の Namespace を設定します。](../../reporting-services/report-server-web-service-net-framework-soap-headers/setting-the-item-namespace-for-the-getproperties-method.md)|<xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドおよび <xref:ReportService2010.ItemNamespaceHeader> SOAP ヘッダーを使用することによって、アイテムのパスまたは ID に基づいたプロパティを取得する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [テクニカル リファレンス (SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  
