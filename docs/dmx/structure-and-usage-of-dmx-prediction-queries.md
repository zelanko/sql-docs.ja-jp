---
title: "構造と DMX 予測クエリの使用状況 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- prediction joins [DMX]
- empty prediction joins [DMX]
- natural prediction joins [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- queries [DMX], prediction queries
- singleton query predictions [DMX]
- Data Mining Extensions [Analysis Services], prediction queries
ms.assetid: 098bdaa6-9e7d-4e13-a9aa-eb17ce1750e6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fca2ff8ef1e6fbe496d412a82c1d2694005ffe6b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="structure-and-usage-of-dmx-prediction-queries"></a>構造と DMX 予測クエリの使用
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、マイニング モデルの結果に基づいて、新しいデータセット内の不明な列の値を予測する、予測クエリのデータ マイニング拡張機能 (DMX) を使用できます。  
  
 使用するクエリの型は、モデルから取得する情報の種類によって異なります。 簡単な予測をリアルタイムで作成する場合、たとえば、Web サイト上の潜在消費者が、自転車購入者の人物像に当てはまるかどうかを判断する場合、単一のクエリを使用します。 データ ソース内に含まれているケースのセットから予測のバッチを作成する場合は、通常の予測クエリを使用します。  
  
## <a name="prediction-types"></a>予測の型  
 DMX を使用して、次の型の予測を作成することができます。  
  
 Prediction join  
 マイニング モデル内に存在するパターンに基づいて、入力データに対する予測を作成するのに使用します。 このクエリ ステートメントが続くことが必要な**ON**をマイニング モデルの列と入力列間の結合条件を指定する句。  
  
 Natural prediction join  
 クエリを実行するテーブル内の列の名前と正確に一致する、マイニング モデル内の列の名前に基づいた予測を作成するのに使用します。 このクエリ ステートメントは必要ありません、 **ON**句、結合条件が自動的に生成するために基づくマイニング モデルの列と入力列の間で一致する名前。  
  
 Empty prediction join  
 最も可能性の高い予測を検出するのに使用します。入力データを指定する必要はありません。 これにより、マイニング モデルの内容にのみ基づいた予測が返されます。  
  
 Singleton query  
 データをクエリに供給することで予測を作成する場合に使用します。 このステートメントは、1 つのケースをクエリに供給することで結果をすばやく得ることができるため便利です。 たとえば、このクエリを使用して、35 歳の既婚女性が自転車を購入する可能性があるかどうかを予測することができます。 このクエリには、外部データ ソースは必要ありません。  
  
## <a name="query-structure"></a>クエリ構造  
 DMX で予測クエリを作成するには、次の要素の組み合わせを使用します。  
  
-   **[フラット化] を選択**  
  
-   **ページのトップへ**  
  
-   **FROM**  *\<モデル >***PREDICTION JOIN**   
  
-   **ON**  
  
-   **どこ**  
  
-   **ORDER BY**  
  
 **選択**予測クエリの要素の列を定義し、結果に表示される式を設定して、次のデータを含めることができます。  
  
-   **予測**または**PredictOnly**マイニング モデルからの列です。  
  
-   予測を作成するのに使用する入力データからの列。  
  
-   データの列を返す関数。  
  
 **FROM** *\<モデル >* **PREDICTION JOIN**要素は、予測を作成するために使用するソース データを定義します。 単一のクエリの場合、これは列に割り当てられた一連の値となります。 空の予測結合の場合は、空のままとなります。  
  
 **ON**要素は、外部データセット内の列をマイニング モデルで定義されている列をマップします。 空の予測結合クエリまたは自然予測結合を作成する場合は、この要素を含める必要はありません。  
  
 使用することができます、**場所**句を予測クエリの結果をフィルター処理します。 使用することができます、**上部**または**ORDER BY**句を最も可能性の高い予測を選択します。 詳細については、これらの句を使用して、次を参照してください。[選択 &#40;DMX&#41;](../dmx/select-dmx.md)です。  
  
 予測ステートメントの構文の詳細については、次を参照してください。 [SELECT FROM &#60; モデル &#62;。予測結合 &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)と[SELECT FROM &60;モデル &#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [DMX の Select ステートメントを理解します](../dmx/understanding-the-dmx-select-statement.md)  
  
  

