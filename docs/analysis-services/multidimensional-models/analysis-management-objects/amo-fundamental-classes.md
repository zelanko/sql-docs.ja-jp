---
title: "AMO 基礎クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data sources [AMO]
- AMO, database objects
- AMO, server objects
- Analysis Management Objects, server objects
- database objects [AMO]
- Analysis Management Objects, database objects
- AMO, data sources
- Analysis Management Objects, data sources
ms.assetid: 440e9287-53a2-4db3-9481-1d2ceb6e5b5a
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2549f0581c8f428e91014c64dc4e8cc90dbe373a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="amo-fundamental-classes"></a>AMO 基礎クラス
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]基本クラスは、分析管理オブジェクト (AMO) での作業の開始点です。 これらのクラスを通じて、アプリケーションで使用するその他のオブジェクトのための環境を整えます。 基礎クラスには、<xref:Microsoft.AnalysisServices.Server>、<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.DataSource>、<xref:Microsoft.AnalysisServices.DataSourceView> などのオブジェクトが含まれます。  
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![AMO 基礎クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-fundamentalclasses.gif "AMO 基礎クラス")  
  
 このトピックには、次のセクションが含まれます。  
  
-   [Server オブジェクト](#ServerObjects)  
  
-   [データベース オブジェクト](#DatabaseObjects)  
  
-   [データ ソース オブジェクトと DataSourceView オブジェクト](#DSandDSV)  
  
##  <a name="ServerObjects"></a>Server オブジェクト  
 さらに、次のメソッドにアクセスできるようになります。  
  
-   接続の管理 (Connect、Disconnect、Reconnect、GetConnectionState)  
  
-   トランザクションの管理 (BeginTransaction、CommitTransaction、RollbackTransaction)  
  
-   バックアップおよび復元  
  
-   DDL の実行 (Execute、CancelCommand、SendXmlaRequest、StartXmlaRequest)  
  
-   メタデータの管理 (UpdateObjects、Validate)  
  
 サーバーに接続するには、ADOMD.NET や OLEDB で使用されるような標準の接続文字列が必要です。 詳細については、次を参照してください。<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>です。 サーバーの名前は接続文字列として指定できます。その際、接続文字列の形式を使用する必要はありません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Server>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
##  <a name="DatabaseObjects"></a>データベース オブジェクト  
 アプリケーションで <xref:Microsoft.AnalysisServices.Database> オブジェクトを操作するには、親サーバーのデータベース コレクションからデータベースのインスタンスを取得する必要があります。 データベースを作成するには、<xref:Microsoft.AnalysisServices.Database> オブジェクトをサーバーのデータベース コレクションに追加し、新しいインスタンスでサーバーを更新します。 データベースを削除するには、削除する <xref:Microsoft.AnalysisServices.Database> オブジェクトの Drop メソッドを使用します。  
  
 データベースをバックアップするときには、<xref:Microsoft.AnalysisServices.Database> オブジェクトまたは <xref:Microsoft.AnalysisServices.Server> オブジェクトの BackUp メソッドを使用できます。ただし、データベースの復元は、<xref:Microsoft.AnalysisServices.Server> オブジェクトの Restore メソッドでしか行えません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Database>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
##  <a name="DSandDSV"></a>データ ソース オブジェクトと DataSourceView オブジェクト  
 データ ソースは、データベース クラスの <xref:Microsoft.AnalysisServices.DataSourceCollection> を使用して管理します。 <xref:Microsoft.AnalysisServices.DataSource> のインスタンスを作成するには、<xref:Microsoft.AnalysisServices.DataSourceCollection> オブジェクトの Add メソッドを使用します。 <xref:Microsoft.AnalysisServices.DataSource> のインスタンスを削除するには、<xref:Microsoft.AnalysisServices.DataSourceCollection> オブジェクトの Remove メソッドを使用します。  
  
 <xref:Microsoft.AnalysisServices.DataSourceView> オブジェクトは、データベース クラスの <xref:Microsoft.AnalysisServices.DataSourceViewCollection> オブジェクトを使用して管理します。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.DataSource>」の「<xref:Microsoft.AnalysisServices.DataSourceView>」および「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO 基本オブジェクトのプログラミング](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md)  
  
  
