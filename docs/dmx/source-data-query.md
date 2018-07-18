---
title: '&lt;ソース データ クエリ&gt;|Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fdd0a3091440295e393d969f1b8161b83fb58d95
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38063962"
---
# <a name="ltsource-data-querygt"></a>&lt;ソース データ クエリ&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング モデルをトレーニングし、マイニング モデルから予測を作成、外部にあるデータにアクセスする必要がある、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。 使用する、\<ソース データ クエリ > 句でのデータ マイニング拡張機能 (DMX) をこの外部データを定義します。 [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md)、 [SELECT FROM&#60;モデル&#62;PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)、および[SELECT FROM NATURAL PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)ステートメントはすべて**\<ソース データ クエリ >** します。  
  
## <a name="query-types"></a>クエリの種類  
 ソース データの指定には、最も一般的な次の 3 つの方法があります。  
  
 [OPENQUERY &AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-openquery.md)  
 このステートメントのインスタンスの外部にあるデータ照会[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、既存のデータ ソースを使用しています。  
  
 中に**OPENQUERY**を関数のような**OPENROWSET**、 **OPENQUERY**次の利点があります。  
  
-   DMX クエリが簡単に使用して記述**OPENQUERY**します。 クエリを記述するたびに新しい接続文字列を作成する代わりに、データ ソース内の既存の接続文字列を利用できます。 データ ソース オブジェクトは、各ユーザーのデータ アクセスを制御することもできます。  
  
-   管理者は、サーバー上のデータがアクセスされる方法を制御しやすくなります。 たとえば、管理者は、サーバーに読み込まれるプロバイダーや、アクセスできる外部データを管理できます。  
  
 [OPENROWSET &AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-openrowset.md)  
 このステートメントのインスタンスの外部にあるデータ照会[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、既存のデータ ソースを使用しています。  
  
 [図形&AMP;#40;DMX&AMP;#41;](../dmx/source-data-query-shape.md)  
 このステートメントは複数のデータ ソースをクエリして、入れ子になったテーブルを作成します。 使用して**図形**、1 つの階層テーブルに複数のソースからデータを結合することができます。 これは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の機能を利用して、テーブル内にテーブルを埋め込むことによってテーブルを入れ子にします。  
  
 ソース データの指定には、次のオプションを使用することもできます。  
  
-   すべての有効な DMX ステートメント  
  
-   すべての有効な多次元式 (MDX) ステートメント  
  
-   ストアド プロシージャを返すテーブル  
  
-   XML for Analysis (XMLA) 行セット  
  
-   行セット パラメーター  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [入れ子になったテーブル&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)  
  
  
