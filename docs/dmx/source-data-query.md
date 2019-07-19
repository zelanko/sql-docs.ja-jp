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
ms.openlocfilehash: 83dbe0c2ea6eb066f208223acd2c6062f964fcf3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938082"
---
# <a name="ltsource-data-querygt"></a>&lt;ソース データ クエリ&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング モデルをトレーニングし、マイニング モデルから予測を作成、外部にあるデータにアクセスする必要がある、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。 使用する、\<ソース データ クエリ > 句でのデータ マイニング拡張機能 (DMX) をこの外部データを定義します。 [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md)、 [SELECT FROM&#60;モデル&#62;PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)、および[SELECT FROM NATURAL PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)ステートメントはすべて **\<ソース データ クエリ >** します。  
  
## <a name="query-types"></a>クエリの種類  
 ソース データの指定には、最も一般的な次の 3 つの方法があります。  
  
 [OPENQUERY &#40;DMX&#41;](../dmx/source-data-query-openquery.md)  
 このステートメントのインスタンスの外部にあるデータ照会[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、既存のデータ ソースを使用しています。  
  
 中に**OPENQUERY**を関数のような**OPENROWSET**、 **OPENQUERY**次の利点があります。  
  
-   DMX クエリが簡単に使用して記述**OPENQUERY**します。 新しい接続を作成する代わりに文字列クエリを記述するたびに、データ ソースで既存の接続文字列の利点を行うことができます。 データ ソース オブジェクトは、各ユーザーのデータ アクセスを制御することもできます。  
  
-   管理者は、サーバー上のデータへのアクセス方法より詳細に制御を持ちます。 たとえば、管理者は、サーバーに読み込まれるプロバイダーや、アクセスできる外部データを管理できます。  
  
 [OPENROWSET &#40;DMX&#41;](../dmx/source-data-query-openrowset.md)  
 このステートメントのインスタンスの外部にあるデータ照会[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、既存のデータ ソースを使用しています。  
  
 [図形&#40;DMX&#41;](../dmx/source-data-query-shape.md)  
 このステートメントは複数のデータ ソースをクエリして、入れ子になったテーブルを作成します。 使用して**図形**、1 つの階層テーブルに複数のソースからデータを結合することができます。 これは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の機能を利用して、テーブル内にテーブルを埋め込むことによってテーブルを入れ子にします。  
  
 ソース データを指定するには、次のオプションを使用することもできます。  
  
-   有効な DMX ステートメント  
  
-   すべての有効な多次元式 (MDX) ステートメント  
  
-   ストアド プロシージャを返すテーブル  
  
-   XML for Analysis (XMLA) 行セット  
  
-   行セット パラメーター  
  
## <a name="see-also"></a>関連項目  
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [入れ子になったテーブル&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)  
  
  
