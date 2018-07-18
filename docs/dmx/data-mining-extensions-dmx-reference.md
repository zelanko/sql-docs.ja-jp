---
title: データ マイニング拡張機能 (DMX) リファレンス |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dcf3231fbff0ec4c3ea32e94f7b974a62faf05e6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38032728"
---
# <a name="data-mining-extensions-dmx-reference"></a>データ マイニング拡張機能 (DMX) リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング拡張機能 (DMX) のデータ マイニング モデルの作成し、操作に使用できる言語は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]します。 DMX を使用して、新しいデータ マイニング モデルの構造の作成、これらのモデルの学習、およびモデルの参照、管理、予測を行うことができます。 DMX は、データ定義言語 (DDL) ステートメント、データ操作言語 (DML) ステートメント、および関数と演算子で構成されています。  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Microsoft OLE DB for Data Mining 仕様  
 データ マイニング機能[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]に準拠するように構築された、 [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB for Data Mining 仕様です。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB for Data Mining 仕様は、次を定義します。  
  
-   データ マイニング モデルを定義する情報を保持するための構造。  
  
-   データ  マイニング モデルの作成および使用のための言語。  
  
 この仕様では、データ マイニングの基礎がデータ マイニング モデル仮想オブジェクトとして定義されます。 データ マイニング モデル オブジェクトは、特定のマイニング モデルに関する既知の事柄をすべてカプセル化します。 データ マイニング モデル オブジェクトは SQL テーブルのような構造になっており、モデルを説明する列、データ型、およびメタ情報から構成されています。 この構造により、SQL の拡張版である DMX 言語を使用して、モデルを作成、使用することができるようになります。  
  
 **詳細情報:** [マイニング構造&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
##  <a name="BKMK_DMXStatements"></a> DMX ステートメント  
 DMX ステートメントを使用して、データ マイニング モデルの作成、処理、削除、コピー、参照、および予測を行うことができます。 DMX にはデータ定義ステートメントおよびデータ操作ステートメントの 2 種類のステートメントがあります。 いずれかのステートメントを使用して、各種のタスクを実行することができます。  
  
 以下のセクションでは、DMX ステートメントの使用に関する詳細について説明します。  
  
-   [データ定義ステートメント](#BKMK_DDL)  
  
-   [データ操作ステートメント](#BKMK_DML)  
  
-   [クエリの基礎](#BKMK_Queries)  
  
###  <a name="BKMK_DDL"></a> データ定義ステートメント  
 新しいマイニング構造とマイニング モデルの作成および定義、マイニング モデルとマイニング構造のインポートおよびエクスポート、データベースからの既存のモデルの削除を行うには、DMX でデータ定義ステートメントを使用します。 DMX でのデータ定義ステートメントは、データ定義言語 (DDL) の一部です。  
  
 DMX でデータ定義ステートメントを使用して、次のタスクを実行することができます。  
  
-   使用してマイニング構造を作成、 [CREATE MINING STRUCTURE](../dmx/create-mining-structure-dmx.md)ステートメントを使用して、マイニング構造にマイニング モデルを追加、 [ALTER MINING STRUCTURE](../dmx/alter-mining-structure-dmx.md)ステートメント。  
  
-   使用して、マイニング モデルと関連するマイニング構造を同時に作成、 [CREATE MINING MODEL](../dmx/create-mining-model-dmx.md)空のデータ マイニング モデル オブジェクトを構築するステートメント。  
  
-   使用して、マイニング モデルと関連するマイニング構造をファイルにエクスポート、[エクスポート](../dmx/export-dmx.md)ステートメント。 使用して、EXPORT ステートメントによって作成されるファイルから、マイニング モデルと関連するマイニング構造をインポート、[インポート](../dmx/import-dmx.md)ステートメント。  
  
-   新しいモデルでは、既存のマイニング モデルの構造にコピーし、学習させる、同じデータを使用して、 [SELECT INTO](../dmx/select-into-dmx.md)ステートメント。  
  
-   使用して、データベースからマイニング モデルを完全に削除、 [DROP MINING MODEL](../dmx/drop-mining-model-dmx.md)ステートメント。 使用して、データベースからマイニング構造とそのすべての関連マイニング モデルを完全に削除、 [DROP MINING STRUCTURE](../dmx/drop-mining-structure-dmx.md)ステートメント。  
  
 DMX ステートメントを使用して実行できるデータ マイニング タスクの詳細については、次を参照してください。[データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)します。  
  
 [DMX ステートメントに戻る](#BKMK_DMXStatements)  
  
###  <a name="BKMK_DML"></a> データ操作ステートメント  
 既存のマイニング モデルの使用、モデルの参照、およびモデルに対する予測の作成を行うには、DMX でデータ操作ステートメントを使用します。 DMX でのデータ操作ステートメントは、データ操作言語 (DML) の一部です。  
  
 DMX でデータ操作ステートメントを使用して、次のタスクを実行することができます。  
  
-   使用してマイニング モデルをトレーニング、 [INSERT INTO](../dmx/insert-into-dmx.md)ステートメント。 これにより、実際のソース データがデータ マイニング モデル オブジェクトに挿入されることはありませんが、アルゴリズムが作成するマイニング モデルを説明する抽象概念が作成されます。 INSERT INTO ステートメントに対するソース クエリについては、「 [\<ソース データ クエリ >](../dmx/source-data-query.md)します。  
  
-   モデルのトレーニング中に計算され、ソース データの統計情報など、データ マイニング モデルに格納される情報を参照する SELECT ステートメントを拡張します。 以下は、SELECT ステートメントの機能を拡張に含めることができる句です。  
  
    -   [SELECT DISTINCT FROM&#60;モデル&#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [SELECT FROM&#60;モデル&#62;します。コンテンツ&#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
    -   [SELECT FROM&#60;モデル&#62;します。ケース&#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)  
  
    -   [SELECT FROM&#60;モデル&#62;します。SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [SELECT FROM&#60;モデル&#62;します。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   使用して既存のマイニング モデルに基づく予測を作成、 [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) SELECT ステートメントの句。 PREDICTION JOIN ステートメントに対するソース クエリについては、「 [\<ソース データ クエリ >](../dmx/source-data-query.md)します。  
  
-   使用して、モデルまたは構造からトレーニング済みのすべてのデータを削除、[削除&#40;DMX&#41; ](../dmx/delete-dmx.md)ステートメント。  
  
 DMX ステートメントを使用して実行できるデータ マイニング タスクの詳細については、次を参照してください。[データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)します。  
  
 [DMX ステートメントに戻る](#BKMK_DMXStatements)  
  
###  <a name="BKMK_Queries"></a> DMX クエリの基礎  
 SELECT ステートメントは、ほとんどの DMX クエリの基礎です。 これらのステートメントで使用する句によって、マイニング モデルの参照、コピー、および予測を行うことができます。 予測クエリでは、既存のマイニング モデルに基づいて予測を作成するのに選択の形式を使用します。 関数を使用することで、データ マイニング モデルの固有の機能では行えないマイニング モデルの参照およびクエリを行うことができます。  
  
 DMX 関数を使用すると、モデルの学習中に検出された情報の取得および新しい情報の計算を行うことができます。 これらの関数は、予測の根拠となるデータや正確性を説明する統計を返したり、予測に対するより広範な説明を返すなど、多くの目的で使用することができます。  
  
 **詳細については****情報:** [Select ステートメントを DMX を理解する](../dmx/understanding-the-dmx-select-statement.md)、[一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)、 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)、[データ マイニング拡張機能&#40;DMX&#41;関数リファレンス  ](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
 [DMX ステートメントに戻る](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
