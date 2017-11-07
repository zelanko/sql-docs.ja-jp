---
title: "Analysis Services のスキーマ行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21cafe5519f9e657a95578aeccbc5773f8eaee97
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services のスキーマ行セット
  スキーマ行セットは、Analysis Services オブジェクトとサーバーの状態に関する情報 (データベース スキーマ、アクティブ セッション、接続、コマンド、サーバー上で実行されるジョブなど) を格納する定義済みのテーブルです。 スキーマ行セットのテーブルに対しては、SQL Server Management Studio の XML/A スクリプト ウィンドウでクエリを実行できます。また、スキーマ行セットに対して DMV クエリを実行したり、スキーマ行セットの情報を保持するカスタム アプリケーションを作成したりできます (レポートの作成に使用できるディメンションの一覧を取得するレポート アプリケーションなど)。  
  
> [!NOTE]  
>  スキーマ行セットは、XML/A で使用する場合のスクリプトを作成で返される情報、*結果*のパラメーター、 [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドはこれで説明されている行セット列のレイアウトに従って構成されています参照してください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーでは、「XML for Analysis 仕様」で定められた行セットがサポートされています。 XMLA プロバイダーでは、OLE DB、OLE DB for OLAP、および OLE DB for Data Mining の各データ ソース プロバイダーに対する標準のスキーマ行セットも一部サポートされています。 サポートされている行セットについては、次の各トピックを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[XML for Analysis スキーマ行セット](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|XMLA プロバイダーによってサポートされている XMLA 行セットについて説明します。|  
|[OLE DB スキーマ行セット](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB スキーマ行セットについて説明します。|  
|[OLE DB for OLAP スキーマ行セット](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB for OLAP スキーマ行セットについて説明します。|  
|[データ マイニング スキーマ行セット](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|XMLA プロバイダーによってサポートされているデータ マイニング スキーマ行セットについて説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ アクセスと #40 です。Analysis Services - 多次元データ &#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [動的管理ビュー (DMV) を使用した Analysis Services の監視](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

