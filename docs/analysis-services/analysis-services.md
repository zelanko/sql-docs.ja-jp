---
title: "Analysis Services |Microsoft ドキュメント"
ms.date: 05/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
caps.latest.revision: 60
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8c3a514f91e9af8de54fdbd4d9ef851c72f1911e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="what-is-analysis-services"></a>Analysis Services とは
  Analysis Services は、意思決定支援とビジネスの分析、Reporting Services レポート、ビジネス レポートおよび Power BI では、Excel などのクライアント アプリケーションの分析データを提供およびその他のデータの視覚化ツールで使用される分析データ エンジンです。  
  
 一般的なワークフローには、多次元形式または表形式データ モデル、内部設置型 SQL Server Analysis Services または Azure Analysis Services サーバー インスタンスにデータベースとしてモデルを展開する、定期的なデータの処理を設定する、割り当ての作成が含まれています。エンドユーザーによってデータ アクセスを許可する権限です。 準備完了である場合は、セマンティック データ モデルをデータ ソースとして Analysis Services をサポートする任意のクライアント アプリケーションによってアクセスできます。  
 
## <a name="analysis-services-on-premises-and-in-the-cloud"></a>オンプレミスとクラウドの Analysis Services
Analysis Services がクラウドで Azure のサービスとして使用できるようになりました。 Azure Analysis Services には、表形式モデル 1200 以降の互換性レベルがサポートしています。 DirectQuery、パーティション、行レベルのセキュリティ、双方向のリレーションシップ、および翻訳がすべてサポートされます。 詳細を確認し、無料版をお試しになる場合は、「[Azure Analysis Services](https://azure.microsoft.com/en-us/services/analysis-services/)」を参照してください。 
  
## <a name="server-mode"></a>サーバー モード  
 SQL Server セットアップを使用して Analysis Services のインストール、構成時に指定そのインスタンスのサーバー モードします。  各モードには、特定の Analysis Services ソリューションに特有の機能が含まれています。   
  
-   **表形式モード**- 実装のインメモリ リレーショナル データ モデリング構造 (モデル、テーブル、列、メジャー、階層)。  

-   **多次元モードとデータ マイニング モード** - OLAP モデリング構造 (キューブ、ディメンション、メジャー) を実行します。 

-   **Power Pivot モード**-SharePoint の Power Pivot の実装と Excel のデータ モデル (Power Pivot for SharePoint は、読み込み、クエリ、およびデータ モデルを SharePoint でホストされている更新の中間層のデータ エンジンです)。  
  
 1 つのインスタンスを構成するとき、利用できるモードは 1 つだけです。後で変更することはできません。  同じサーバーで複数のインスタンスを異なるモードでインストールできますが、セットアップを実行し、インスタンスごとに構成設定を指定する必要があります。 詳細な情報と各モードで提供されるさまざまな機能の比較では、次を参照してください。[を比較する表形式および多次元ソリューション](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)です。
  
## <a name="authoring-and-managing-solutions"></a>作成およびソリューションの管理  
 モデルを作成し、サーバーに配置するには、いずれか、テーブルまたは多次元およびデータ マイニング プロジェクト テンプレートを選択する SQL Server Data Tools を使用します。 プロジェクト テンプレートには、モデルで必要とされるすべてのオブジェクトのフォルダーが含まれています。 多くのデータ ソース、リレーションシップ、メジャー、およびロールに接続するなどの基本的な要素を作成するウィザードとデザイナーのヘルプ。 モデル データベースがサーバーに展開した後は、データ処理の構成、監視、およびサーバーとデータベースを管理する SQL Server Management Studio (SSMS) を使用します。 詳細については、次を参照してください。[ツールと Analysis Services で使用されるアプリケーション](../analysis-services/tools-and-applications-used-in-analysis-services.md)です。 
  
## <a name="documentation-by-area"></a>領域別のドキュメント  
一般的な Azure Analysis Services に関するドキュメントは、Azure のドキュメントに含まれて。 また、SQL Server Analysis Services のドキュメントが SQL のドキュメントに含まれる。 、には、少なくとも、表形式モデルの作成方法と、プロジェクトの配置が使用しているどのようなプラットフォームに関係なくほとんど同じです。  
   
*  [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)
*  [SQL Server Analysis Services の新機能](../analysis-services/what-s-new-in-analysis-services.md)   
*  [テーブル ソリューションと多次元ソリューションの比較](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
*  [テーブル モデル](../analysis-services/tabular-models/tabular-models-ssas.md)  
*  [多次元モデル](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
*  [データ マイニング](../analysis-services/data-mining/data-mining-ssas.md)  
*  [Power Pivot for SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
*  [インスタンスの管理](../analysis-services/instances/analysis-services-instance-management.md)    
*  [チュートリアル](../analysis-services/analysis-services-tutorials-ssas.md)   
*  [開発者向けドキュメント](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
*  [テクニカル リファレンス (SSAS)](../analysis-services/powershell/technical-reference-ssas.md)

