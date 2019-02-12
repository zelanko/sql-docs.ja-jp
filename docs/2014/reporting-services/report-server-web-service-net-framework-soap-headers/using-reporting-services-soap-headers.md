---
title: Reporting Services の SOAP ヘッダーの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3a9e61cc8cc546156d24c209a68c3a523a0f8a29
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015063"
---
# <a name="using-reporting-services-soap-headers"></a>Reporting Services の SOAP ヘッダーの使用
  SOAP を使用した Web サービス メソッドとの通信では、標準形式に従います。 この標準形式の一部は、XML ドキュメントでエンコードされるデータです。 XML ドキュメントは、ルート **Envelope** 要素で構成され、さらにその要素は必須の **Body** 要素および省略可能な **Header** 要素で構成されます。 **Body** 要素には、メッセージ固有のデータが含まれます。 省略可能な **Header** 要素には、特定のメッセージに直接関連しない追加情報を含めることができます。 **Header** 要素の各子要素は、SOAP ヘッダーと呼ばれます。  
  
 SOAP ヘッダーには、メッセージに関連するデータを含めることができますが、一般的には Web サーバー内のインフラストラクチャによって処理される情報が含まれます。  
  
 レポート サーバー Web サービスでは、SOAP ヘッダーで使用される複数のクラス、つまり <xref:ReportService2005.BatchHeader>、<xref:ReportService2010.ItemNamespaceHeader>、<xref:ReportService2010.ServerInfoHeader>、<xref:ReportService2010.TrustedUserHeader>、および <xref:ReportExecution2005.ExecutionHeader> を定義します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[メソッドのバッチ処理](batching-methods.md)|<xref:ReportService2005.BatchHeader> を使用して、複数の操作を 1 つのトランザクションにまとめる方法を説明します。|  
|[実行状態の識別](identifying-execution-state.md)|**Session Header** を使って、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] でセッション状態を管理する方法について説明します。|  
|[GetProperties メソッドのアイテム名前空間の設定](setting-the-item-namespace-for-the-getproperties-method.md)|<xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドおよび <xref:ReportService2010.ItemNamespaceHeader> SOAP ヘッダーを使用することによって、アイテムのパスまたは ID に基づいたプロパティを取得する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [テクニカル リファレンス (SSRS)](../technical-reference-ssrs.md)  
  
  
