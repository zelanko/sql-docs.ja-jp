---
title: SQL Server Analysis Services の概要 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: overview
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 704c2f1638676bd838c7aac367a1b610143fd85d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="about-sql-server-analysis-services"></a>SQL Server Analysis Services の概要

Analysis Services は、意思決定支援とビジネスの分析で使用される分析データ エンジンです。 提供エンタープ ライス セマンティック データ モデルのビジネス レポートおよび Power BI で Excel、Reporting Services レポート、およびその他のデータの視覚化ツールなどのクライアント アプリケーション。  

一般的なワークフローには、Visual Studio でデータを表形式または多次元モデル プロジェクトを作成、モデルを展開するサーバー インスタンスにデータベースとして、定期的なデータの処理を設定およびエンドユーザーによってデータ アクセスを許可するアクセス許可の割り当てが含まれています。 準備完了である場合は、セマンティック データ モデルをデータ ソースとして Analysis Services をサポートするクライアント アプリケーションによってアクセスできます。  

Analysis Services は、次の 2 つの異なるプラットフォームで使用できます。 

**Azure Analysis Services** -表形式モデル 1200 以降の互換性レベルをサポートしています。 DirectQuery、パーティション、行レベルのセキュリティ、双方向のリレーションシップ、および翻訳がすべてサポートされます。 詳細については、次を参照してください。 [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)です。

**SQL Server Analysis Services** -SharePoint のすべての互換性レベル、多次元モデル、データ マイニング、および Power Pivot の表形式モデルをサポートしています。
 
 ## <a name="documentation-by-area"></a>領域別のドキュメント  
般的に、 [Azure Analysis Services に関するドキュメントは](https://docs.microsoft.com/azure/analysis-services/) Azure のドキュメントに含まれます。 クラウドに、表形式モデルに関心がある場合は、ある開始することをお勧めします。 この記事とこのセクションのドキュメントでは、SQL Server Analysis Services のほとんどの場合です。 しかし、少なくとも表形式モデルに関しては、どのプラットフォームを使用しているかに関わらず、プロジェクトの作成方法と展開方法は同じです。 詳細については、これらのセクションをご覧ください。

   
*  [テーブル ソリューションと多次元ソリューションの比較](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
*  [SQL Server Analysis Services をインストールします。](../analysis-services/instances/install-windows/install-analysis-services.md)
*  [テーブル モデル](../analysis-services/tabular-models/tabular-models-ssas.md)  
*  [多次元モデル](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
*  [データ マイニング](../analysis-services/data-mining/data-mining-ssas.md)  
*  [Power Pivot for SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
*  [チュートリアル](../analysis-services/analysis-services-tutorials-ssas.md)   
*  [サーバーの管理](../analysis-services/instances/analysis-services-instance-management.md)    
*  [開発者向けドキュメント](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
*  [テクニカル リファレンス](../analysis-services/powershell/technical-reference-ssas.md)

参照

[Azure Analysis Services のドキュメント](https://docs.microsoft.com/azure/analysis-services/)   
[SQL Server のドキュメント](../sql-server/sql-server-technical-documentation.md)
