---
title: Analysis Services のスキーマ行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f2444880b28584a2a9ea70a3f229a94f0d8edf34
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services のスキーマ行セット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  スキーマ行セットは、Analysis Services オブジェクトとサーバーの状態に関する情報 (データベース スキーマ、アクティブ セッション、接続、コマンド、サーバー上で実行されるジョブなど) を格納する定義済みのテーブルです。 スキーマ行セットのテーブルに対しては、SQL Server Management Studio の XML/A スクリプト ウィンドウでクエリを実行できます。また、スキーマ行セットに対して DMV クエリを実行したり、スキーマ行セットの情報を保持するカスタム アプリケーションを作成したりできます (レポートの作成に使用できるディメンションの一覧を取得するレポート アプリケーションなど)。  
  
> [!NOTE]  
>  スキーマ行セットは、XML/A で使用する場合のスクリプトを作成で返される情報、*結果*のパラメーター、 [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドはこのセクションで説明されている行セット列のレイアウトに従って構成されています。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーでは、「XML for Analysis 仕様」で定められた行セットがサポートされています。 XMLA プロバイダーでは、OLE DB、OLE DB for OLAP、および OLE DB for Data Mining の各データ ソース プロバイダーに対する標準のスキーマ行セットも一部サポートされています。 サポートされている行セットについては、次の各トピックを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[XML for Analysis スキーマ行セット](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|XMLA プロバイダーによってサポートされている XMLA 行セットについて説明します。|  
|[OLE DB スキーマ行セット](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB スキーマ行セットについて説明します。|  
|[OLE DB for OLAP スキーマ行セット](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB for OLAP スキーマ行セットについて説明します。|  
|[データ マイニング スキーマ行セット](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|XMLA プロバイダーによってサポートされているデータ マイニング スキーマ行セットについて説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ アクセスと &#40;です。Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [使用して動的管理ビュー &#40;です。 Dmv&#41; Analysis Services を監視するには](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
