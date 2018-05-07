---
title: '&lt;ソース データ クエリ&gt;|Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- data sources [DMX]
- predictions [DMX]
- source data query element
- queries [DMX], source data
- external data access [DMX]
- <source data query> element
- training mining models
ms.assetid: 9dce5e37-1354-4d28-87c2-f9c419cb5b09
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 25285a04adf2c8547f9a9a50d07e7c3ed9fce54b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsource-data-querygt"></a>&lt;ソース データ クエリ&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング モデルのトレーニングをマイニング モデルから予測の作成は、外部にあるデータにアクセスする必要がある、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。 使用する、\<ソース データ クエリ > 句でデータ マイニング拡張機能 (DMX) をこの外部データを定義します。 [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md)、 [SELECT FROM&#60;モデル&#62;PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)、および[SELECT FROM NATURAL PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)ステートメントはすべて**\<ソース データ クエリ >** です。  
  
## <a name="query-types"></a>クエリの種類  
 ソース データの指定には、最も一般的な次の 3 つの方法があります。  
  
 [OPENQUERY &AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-openquery.md)  
 このステートメントは、外部のインスタンスにデータを照会する[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、既存のデータ ソースを使用しています。  
  
 中に**OPENQUERY**の関数に似ています**OPENROWSET**、 **OPENQUERY**次の利点があります。  
  
-   DMX クエリを使用して記述をはるかに簡単**OPENQUERY**です。 クエリを記述するたびに新しい接続文字列を作成する代わりに、データ ソース内の既存の接続文字列を利用できます。 データ ソース オブジェクトは、各ユーザーのデータ アクセスを制御することもできます。  
  
-   管理者は、サーバー上のデータがアクセスされる方法を制御しやすくなります。 たとえば、管理者は、サーバーに読み込まれるプロバイダーや、アクセスできる外部データを管理できます。  
  
 [OPENROWSET &AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-openrowset.md)  
 このステートメントは、外部のインスタンスにデータを照会する[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、既存のデータ ソースを使用しています。  
  
 [図形&AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-shape.md)  
 このステートメントは複数のデータ ソースをクエリして、入れ子になったテーブルを作成します。 使用して**図形**、1 つの階層テーブルに複数のソースからデータを組み合わせることができます。 これは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の機能を利用して、テーブル内にテーブルを埋め込むことによってテーブルを入れ子にします。  
  
 ソース データの指定には、次のオプションを使用することもできます。  
  
-   すべての有効な DMX ステートメント  
  
-   すべての有効な多次元式 (MDX) ステートメント  
  
-   ストアド プロシージャを返すテーブル  
  
-   XML for Analysis (XMLA) 行セット  
  
-   行セット パラメーター  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [入れ子になったテーブル&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)  
  
  
