---
title: マイニング モデルに対するコンテンツ クエリを作成 |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a845a81634cbd81a72ab6ecc54f137df475158f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="create-a-content-query-on-a-mining-model"></a>マイニング モデルのコンテンツ クエリの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  AMO や XML/A を使用すると、プログラムでマイニング モデル コンテンツにクエリを実行できますが、DMX を使用してクエリを作成する方が簡単です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスへの接続を確立し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]によって提供される DMV を使用してクエリを作成することにより、データ マイニング スキーマ行セットに対するクエリを作成することもできます。  
  
 次の手順では、DMX を使用してマイニング モデルに対するクエリを作成する方法と、データ マイニング スキーマ行セットに対するクエリを実行する方法について説明します。  
  
 XML/A を使用して類似のクエリを作成する方法の例については、「 [XMLA を使用したデータ マイニング クエリの作成](../../analysis-services/data-mining/create-a-data-mining-query-by-using-xmla.md)」を参照してください。  
  
## <a name="querying-data-mining-model-content-by-using-dmx"></a>DMX を使用したデータ マイニング モデル コンテンツのクエリ  
  
#### <a name="to-create-a-dmx-model-content-query"></a>DMX モデル コンテンツ クエリを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  **[テンプレート エクスプローラー]** ペインで、キューブ アイコンをクリックして一覧を変更し、Analysis Services テンプレートを表示します。  
  
3.  テンプレート カテゴリの一覧で、 **[DMX]**、 **[モデル コンテンツ]** の順に展開し、 **[コンテンツ クエリ]** をダブルクリックします。  
  
4.  **[Analysis Services への接続]** ダイアログ ボックスで、クエリを実行するマイニング モデルを含むインスタンスを選択し、 **[接続]** をクリックします。  
  
     コード エディターに **[コンテンツ クエリ]** テンプレートが表示されます。 メタデータ ペインに、現在のデータベースで使用可能なモデルが一覧表示されます。 データベースを変更するには、 **[使用できるデータベース]** の一覧から別のデータベースを選択します。  
  
5.  行で、マイニング モデルの名前を入力`FROM`[*\<マイニング モデル, name, MyModel >*]`.CONTENT`です。 マイニング モデル名にスペースが含まれる場合は、名前を角かっこで囲む必要があります。  
  
     名前を入力せずに、 **オブジェクト エクスプローラー** でマイニング モデルを選択してテンプレートにドラッグすることもできます。  
  
6.  行で、 `SELECT` *\<選択リスト、expr、 \* >* 、マイニング モデル コンテンツ スキーマ行セットの列の名前を入力します。  
  
     マイニング モデル コンテンツ クエリで返すことができる列の一覧については、「[マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
7.  必要に応じて、テンプレートの WHERE 句に条件を入力し、特定のノードや値に対して返される行を制限します。  
  
8.  **[実行]** をクリックします。  
  
## <a name="querying-the-data-mining-schema-rowsets"></a>データ マイニング スキーマ行セットのクエリ  
  
#### <a name="to-create-a-query-against-the-data-mining-schema-rowset"></a>データ マイニング スキーマ行セットに対するクエリを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の **[新しいクエリ]** ツール バーで、 **[Analysis Services DMX クエリ]** または **[Analysis Services MDX クエリ]** をクリックします。  
  
2.  **[Analysis Services への接続]** ダイアログ ボックスで、クエリを実行するオブジェクトを含むインスタンスを選択し、 **[接続]** をクリックします。  
  
     コード エディターに **[コンテンツ クエリ]** テンプレートが表示されます。 メタデータ ペインに、現在のデータベースで使用可能なオブジェクトが一覧表示されます。 データベースを変更するには、 **[使用できるデータベース]** の一覧から別のデータベースを選択します。  
  
3.  クエリ エディターに次のように入力します。  
  
     `SELECT *`  
  
     `FROM $system.DMSCHEMA_MINING_MODEL_CONTENT`  
  
     `WHERE MODEL_NAME = '<model name>'`  
  
4.  **[実行]** をクリックします。  
  
     結果ペインにモデルのコンテンツが表示されます。  
  
    > [!NOTE]  
    >  現在のインスタンスでクエリを実行できるすべてのスキーマ行セットを一覧表示するには、 `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS というクエリを使用します。 データ マイニング固有のスキーマ行セットの一覧については、「 [データ マイニング スキーマ行セット](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル コンテンツ & #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)   
 [データ マイニング スキーマ行セット](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
