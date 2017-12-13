---
title: "Analysis Services のスキーマ行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ed5393a6406aa031f141d6a635f0690983626dd5
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services のスキーマ行セット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]スキーマ行セットは、Analysis Services オブジェクトとサーバーの状態、データベース スキーマ、アクティブなセッション、接続、コマンド、およびサーバー上で実行されるジョブなどに関する情報を含む定義済みのテーブルです。 スキーマ行セットのテーブルに対しては、SQL Server Management Studio の XML/A スクリプト ウィンドウでクエリを実行できます。また、スキーマ行セットに対して DMV クエリを実行したり、スキーマ行セットの情報を保持するカスタム アプリケーションを作成したりできます (レポートの作成に使用できるディメンションの一覧を取得するレポート アプリケーションなど)。  
  
> [!NOTE]  
>  スキーマ行セットは、XML/A で使用する場合のスクリプトを作成で返される情報、*結果*のパラメーター、 [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドはこれで説明されている行セット列のレイアウトに従って構成されています参照してください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーでは、「XML for Analysis 仕様」で定められた行セットがサポートされています。 XMLA プロバイダーでは、OLE DB、OLE DB for OLAP、および OLE DB for Data Mining の各データ ソース プロバイダーに対する標準のスキーマ行セットも一部サポートされています。 サポートされている行セットについては、次の各トピックを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[XML for Analysis Schema 行セット](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|XMLA プロバイダーによってサポートされている XMLA 行セットについて説明します。|  
|[OLE DB Schema 行セット](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB スキーマ行セットについて説明します。|  
|[OLE DB for OLAP Schema 行セット](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB for OLAP スキーマ行セットについて説明します。|  
|[データ マイニング スキーマ行セット](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|XMLA プロバイダーによってサポートされているデータ マイニング スキーマ行セットについて説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ アクセスと #40 です。Analysis Services - 多次元データ &#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [動的管理ビュー (DMV) を使用した Analysis Services の監視](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
