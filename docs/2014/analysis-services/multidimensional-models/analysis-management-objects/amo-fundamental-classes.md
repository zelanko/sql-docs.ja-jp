---
title: AMO 基礎クラス |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ee31478a526dad385d9721256beebc4324cadb60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174371"
---
# <a name="amo-fundamental-classes"></a>AMO 基礎クラス
  基礎クラスは、分析管理オブジェクト (AMO) を操作するための開始点です。 これらのクラスを通じて、アプリケーションで使用するその他のオブジェクトのための環境を整えます。 基礎クラスには、<xref:Microsoft.AnalysisServices.Server>、<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.DataSource>、<xref:Microsoft.AnalysisServices.DataSourceView> などのオブジェクトが含まれます。  
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![AMO 基礎クラス](../../../analysis-services/dev-guide/media/amo-fundamentalclasses.gif "AMO 基礎クラス")  
  
  
  
##  <a name="ServerObjects"></a> Server オブジェクト  
 さらに、次のメソッドにアクセスできるようになります。  
  
-   接続の管理 (Connect、Disconnect、Reconnect、GetConnectionState)  
  
-   トランザクションの管理 (BeginTransaction、CommitTransaction、RollbackTransaction)  
  
-   バックアップおよび復元  
  
-   DDL の実行 (Execute、CancelCommand、SendXmlaRequest、StartXmlaRequest)  
  
-   メタデータの管理 (UpdateObjects、Validate)  
  
 サーバーに接続するには、ADOMD.NET や OLEDB で使用されるような標準の接続文字列が必要です。 詳細については、「<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>」を参照してください。 サーバーの名前は接続文字列として指定できます。その際、接続文字列の形式を使用する必要はありません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Server>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
##  <a name="DatabaseObjects"></a> データベース オブジェクト  
 アプリケーションで <xref:Microsoft.AnalysisServices.Database> オブジェクトを操作するには、親サーバーのデータベース コレクションからデータベースのインスタンスを取得する必要があります。 データベースを作成するには、<xref:Microsoft.AnalysisServices.Database> オブジェクトをサーバーのデータベース コレクションに追加し、新しいインスタンスでサーバーを更新します。 データベースを削除するには、削除する <xref:Microsoft.AnalysisServices.Database> オブジェクトの Drop メソッドを使用します。  
  
 データベースをバックアップするときには、<xref:Microsoft.AnalysisServices.Database> オブジェクトまたは <xref:Microsoft.AnalysisServices.Server> オブジェクトの BackUp メソッドを使用できます。ただし、データベースの復元は、<xref:Microsoft.AnalysisServices.Server> オブジェクトの Restore メソッドでしか行えません。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Database>」の「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
##  <a name="DSandDSV"></a> データ ソース オブジェクトと DataSourceView オブジェクト  
 データ ソースは、データベース クラスの <xref:Microsoft.AnalysisServices.DataSourceCollection> を使用して管理します。 <xref:Microsoft.AnalysisServices.DataSource> のインスタンスを作成するには、<xref:Microsoft.AnalysisServices.DataSourceCollection> オブジェクトの Add メソッドを使用します。 <xref:Microsoft.AnalysisServices.DataSource> のインスタンスを削除するには、<xref:Microsoft.AnalysisServices.DataSourceCollection> オブジェクトの Remove メソッドを使用します。  
  
 <xref:Microsoft.AnalysisServices.DataSourceView> オブジェクトは、データベース クラスの <xref:Microsoft.AnalysisServices.DataSourceViewCollection> オブジェクトを使用して管理します。  
  
 利用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.DataSource>」の「<xref:Microsoft.AnalysisServices.DataSourceView>」および「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](amo-classes-introduction.md)   
 [AMO 基本オブジェクトのプログラミング](programming-amo-fundamental-objects.md)  
  
  