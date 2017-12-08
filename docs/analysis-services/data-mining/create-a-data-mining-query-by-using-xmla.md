---
title: "XMLA を使用して、データ マイニング クエリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: content queries [DMX]
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 78037aa620ae5a0ed6861d55503e96fd5bb2fb18
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-a-data-mining-query-by-using-xmla"></a>XMLA を使用したデータ マイニング クエリの作成
  AMO、DMX、または XML/A を使用すると、データ マイニング オブジェクトに対するさまざまなクエリを作成できます。  
  
 Analysis Services サーバーとすべてのクライアントの間の通信には、XML が使用されます。 したがって、一般には DMX を使用してコンテンツ クエリを作成する方がはるかに簡単ですが、SOAP プロトコルをサポートするクライアントを使用するか、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で XML/A クエリを作成することにより、XML/A で DISCOVER および COMMAND ステートメントを使用してクエリを作成できます。  
  
 このトピックでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で利用できる XML/A テンプレートを使用して、現在のサーバーに格納されているマイニング モデルに対するモデル コンテンツ クエリを作成する方法について説明します。  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a>XML/A を使用したデータ マイニング スキーマ行セットのクエリ  
  
#### <a name="to-open-an-xmla-template"></a>XML/A テンプレートを開くには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]**をクリックします。  
  
2.  キューブ アイコンをクリックして、Analysis Services テンプレートの一覧を開きます。  
  
3.  テンプレート カテゴリの一覧で **[XMLA]**、 **[スキーマ行セット]**の順に展開し、 **[スキーマ行セットの発見]** をダブルクリックします。コード エディターにこのテンプレートが表示されます。  
  
4.  **[Analysis Services への接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]**をクリックします。 新しいクエリ エディター ウィンドウが開き、 **[スキーマ行セットの発見]** テンプレートの内容が表示されます。  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a>MINING MODEL CONTENT スキーマ行セットから列名を検出するには  
  
1.  **[スキーマ行セットの発見]** テンプレートを開き、 **[実行]**をクリックします。  
  
     **[結果]** ペインに返されるスキーマ行セットの一覧には、現在のインスタンスで入手できるすべての行セットの行セット名と行セット列が含まれます。  
  
2.  **クエリ** ウィンドウで、後にカーソルを置き**\<制限一覧 >**し、enter キーを押して新しい行を追加します。  
  
3.  カーソルを置き、空白行と種類 **\<SchemaName > DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName >**  
  
     制限のセクション全体は次のようになります。  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  **[実行]**をクリックします。  
  
     **[結果]** ペインに、指定したスキーマ行セットの列名の一覧が表示されます。  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a>MINING MODEL CONTENT スキーマ行セットを使用してコンテンツ クエリを作成するには  
  
1.  **[スキーマ行セットの発見]** テンプレートで、"要求の種類" タグの内側のテキストを置き換えて、要求の種類を変更します。  
  
     次の行を置き換えます。  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     置き換えると、次のようになります。  
  
     **\<RequestType > DMSCHEMA_MINING_MODEL_CONTENT\</RequestType >**  
  
2.  制限リストに新しい条件を追加することで、名前でマイニング モデルを指定するように制限リストを変更します。  
  
3.  テンプレートで、`<Restriction List>` の後ろにカーソルを置き、Enter キーを押して新しい行を追加します。  
  
4.  空白行にカーソルを置き、「**<MODEL_NAME>My model name</MODEL_NAME>**」と入力します。  
  
     制限のセクション全体は次のようになります。  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  **[実行]**をクリックします。  
  
     [結果] ペインに、スキーマ定義および指定したモデルの値が表示されます。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)   
 [データ マイニング スキーマ行セット](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
