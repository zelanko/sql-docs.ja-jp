---
title: "Web サービス メソッドの引数を指定する |Microsoft ドキュメント"
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
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
caps.latest.revision: 38
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 43fcfe6eecffdc237366eb7963a5582b1915d363
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="supplying-web-service-method-arguments"></a>Web サービス メソッドの引数の指定
  レポート サーバー Web サービスのメソッドは、SOAP を使用し、HTTP 経由で特定の URL のサービスに対して要求を送信します。 サービスでは、要求を受信し、処理した後、応答を返します。 これらの要求と応答は XML ドキュメント形式です。  
  
## <a name="optional-parameters"></a>省略可能なパラメーター  
 場合によっては、Web サービス メソッドに省略可能な入力パラメーターがあります。 Web サービス メソッドの入力パラメーターが省略可能な場合でもまだことを組み込み、パラメーター値を設定**null** (**Nothing**で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])。 パラメーター値を設定**null**への SOAP 要求にそのパラメーターの要素の値を設定**null**です。  
  
 次の例では、<xref:ReportService2010.ReportingService2010.CreateFolder%2A> メソッドを使用して、Sales フォルダーに Product Sales という新しいフォルダーを作成します。 指定することによって、 **null**フォルダーにないユーザーに固有のプロパティ、フォルダーのプロパティの値を指定します。  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>複合データ型  
 レポート サーバー Web サービスのコア クラスは <xref:ReportService2010.ReportingService2010> です。このクラスは、プロキシ クラスの SOAP 操作または Web メソッドを呼び出すときに使用します。 このクラスとメソッドをサポートするため、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には、Web サービス メソッドの入出力パラメーターに固有であるユーザー定義の複合データ型が含まれます。 これらの複雑なデータ型で開発するときに使用することができますが、生成されたプロキシ クラスの一部である、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]環境。  
  
 プロキシ クラスを生成すると、WSDL ファイルに定義された複合データ型はプロキシのクラスによって表されます。このクラスには、複合データ型のさまざまな SOAP 要素に対応するプロパティが入っています。 一連の複合データ型は、コードで列挙できるオブジェクトの配列になります。 したがって、SOAP メッセージで送信された XML 構造を直接扱う必要がなくなります。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、自動的に変換が行われます。  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
