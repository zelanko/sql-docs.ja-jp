---
title: SELECT FROM&lt;モデル&gt;PREDICTION JOIN (DMX) |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f0778a104383f54cf2798c0d6f51f082926b1fd4
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842165"
---
# <a name="select-from-ltmodelgt-prediction-join-dmx"></a>SELECT FROM&lt;モデル&gt;PREDICTION JOIN (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング モデルを使用して、外部データ ソース内の列の状態を予測します。 **PREDICTION JOIN**ステートメントをモデルに、ソース クエリからは、各ケースに一致します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <select expression list>   
FROM <model> | <sub select> [NATURAL] PREDICTION JOIN   
<source data query> [ON <join mapping list>]   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 任意。 返す行数を指定する整数値です。  
  
 *select 式リスト*  
 マイニング モデルから派生する、列の識別子と式のコンマ区切りのリストです。  
  
 *model*  
 モデル識別子です。  
  
 *sub を選択します。*  
 埋め込まれた select ステートメントです。  
  
 *ソース データ クエリ*  
 ソース クエリです。  
  
 *マッピングのリストを結合*  
 任意。 モデルの列とソース クエリの列を比較する論理演算子です。  
  
 *条件式*  
 任意。 列のリストから返される値を制限する条件です。  
  
 *式 (expression)*  
 任意。 スカラー値を返す式。  
  
## <a name="remarks"></a>コメント  
 ON 句は、ソース クエリの列とマイニング モデルの列の間のマッピングを定義します。 このマッピングは、列は、予測を作成する入力として使用できるようにする、マイニング モデル内の列に、ソース クエリから列を直接に使用されます。 内の列、 \<*マッピングのリストを結合*> 次の例で示すように等号 (=) を使用して関連。  
  
```  
[MiningModel].ColumnA = [source data query].Column1 AND   
[MiningModel].ColumnB = [source data query].Column2 AND  
...  
```  
  
 入れ子になったテーブルを ON 句にバインドする場合、入れ子になった列のレコードが所属するケースをアルゴリズムが正しく識別できるように、キー列をすべての非キー列とバインドします。  
  
 予測結合のソース クエリは、テーブルまたは単一クエリのどちらかにできます。  
  
 テーブル式を返さない予測関数を指定することができます、 \< *select 式リスト*> および\<*条件式*>。  
  
 **NATURAL PREDICTION JOIN**と共に、モデル内の列名に一致するソース クエリから列名が自動的にマップします。 使用する場合**自然予測**ON 句を省略することができます。  
  
 WHERE 条件は、予測可能列または関連列のみに適用できます。  
  
 ORDER by 句は、引数として 1 つの列のみを受け入れることができます。つまり、1 つ以上の列を並べ替えることはできません。  
  
## <a name="example-1-singleton-query"></a>例 1: 単一クエリ  
 次の例は、特定の人物が実際に自転車を購入するかどうかを予測するクエリの作成方法を示します。 このクエリでは、データはテーブルまたはその他のデータ ソースに格納されませんが、クエリに直接入力されます。 クエリ内の人物は、次の特徴を持ちます。  
  
-   35 才  
  
-   持ち家所有  
  
-   2 台の自家用車を所有  
  
-   子供は 2 名  
  
 人が自転車とによって返される、表形式の値のセットを購入するかどうかを示すブール値を返します、クエリの TM Decision Tree マイニング モデルとサブジェクトに関する既知の特性を使用して、 [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md) 、予測が行われた方法を説明する関数。  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  PredictHistogram([Bike Buyer])  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 35 AS [Age],  
  '5-10 Miles' AS [Commute Distance],  
  '1' AS [House Owner Flag],  
  2 AS [Number Cars Owned],  
  2 AS [Total Children]) AS t  
```  
  
## <a name="example-2-using-openquery"></a>例 2: OPENQUERY の使用  
 次の例は、外部データセットに格納されている潜在的な顧客の一覧を使用して、バッチ予測クエリを作成する方法を示します。 インスタンスで定義されているデータ ソース ビューの一部であるため[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、クエリで使用できる[OPENQUERY](../dmx/source-data-query-openquery.md)データを取得します。 テーブル内の列の名前は、マイニング モデルで異なるため、 **ON**句を使用して、モデル内の列に、テーブル内の列をマップする必要があります。  
  
 クエリは、テーブル内の各人物の氏名と共に、各人物が自転車を購入しそうかどうかを示すブール型の列を返します。この場合、0 は "自転車を購入する可能性が低い" こと、1 は "自転車を購入する可能性が高い" ことを示します。 最後の列には、予測結果の確率が含まれます。  
  
```  
SELECT  
  t.[LastName],  
  t.[FirstName],  
  [TM Decision Tree].[Bike Buyer],  
  PredictProbability([Bike Buyer])  
From  
  [TM Decision Tree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [LastName],  
      [FirstName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [Education],  
      [Occupation],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
  [TM Decision Tree].[Gender] = t.[Gender] AND  
  [TM Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM Decision Tree].[Total Children] = t.[TotalChildren] AND  
  [TM Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM Decision Tree].[Education] = t.[Education] AND  
  [TM Decision Tree].[Occupation] = t.[Occupation] AND  
  [TM Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
```  
  
 自転車を購入することが予測される顧客のみにデータセットを制限してから、顧客名で一覧を並べ替えるには、上記の例に WHERE 句と ORDER BY 句を追加します。  
  
```  
WHERE [BIKE Buyer]  
ORDER BY [LastName] ASC  
```  
  
## <a name="example-3-predicting-associations"></a>例 3: アソシエーションの予測  
 次の例は、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムから作成したモデルを使用して予測を作成する方法を示します。 アソシエーション モデルの予測は、関連する製品を推奨するために使用できます。 たとえば、次のクエリでは、共に購入される可能性が最も高い製品を 3 つ返します。  
  
-   Mountain Bottle Cage  
  
-   Mountain Tire Tube  
  
-   Mountain-200  
  
 [Predict &#40;DMX&#41; ](../dmx/predict-dmx.md)関数はポリモーフィックでは、すべての種類のモデルで使用できます。 この関数の引数に値 3 を使用して、クエリから返される項目の数を制限します。 **選択**NATURAL PREDICTION JOIN 句を下記の一覧が予測の入力として使用する値を提供します。  
  
```  
SELECT FLATTENED  
  PREDICT([Association].[v Assoc Seq Line Items], 3)  
FROM  
  [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
  UNION SELECT 'Mountain Tire Tube' AS [Model]  
  UNION SELECT 'Mountain-200' AS [Model]) AS [v Assoc Seq Line Items ]) AS t  
```  
  
 例の結果を次に示します。  
  
|Expression.Model|  
|----------------------|  
|HL Mountain Tire|  
|Water Bottle|  
|Fender Set - Mountain|  
  
 予測可能属性を含む列`[v Assoc Seq Line Items]`テーブルの列は、クエリは、入れ子になったテーブルを含む 1 つの列を返します。 既定では入れ子になったテーブル列の名前は`Expression`します。 使用することができます、プロバイダーが階層的な行セットをサポートしていない場合、 **FLATTENED**キーワードやすく、結果を表示するこの例で示すようにします。  
  
## <a name="see-also"></a>参照  
 [選択&AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
