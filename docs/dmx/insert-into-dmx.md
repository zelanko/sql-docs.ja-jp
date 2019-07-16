---
title: 挿入 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 463bd3ac40a2f90a66457faa9a80b9512b67b53a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937785"
---
# <a name="insert-into-dmx"></a>INSERT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたデータ マイニング オブジェクトを処理します。 マイニング モデルとマイニング構造の処理に関する詳細については、次を参照してください。[処理の要件と考慮事項&#40;データ マイニング&#41;](../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)します。  
  
 マイニング構造が指定された場合、ステートメントはマイニング構造とすべての関連するマイニング モデルを処理します。 マイニング モデルが指定された場合、ステートメントはマイニング モデルだけを処理します。  
  
## <a name="syntax"></a>構文  
  
```  
  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure> (<mapped model columns>) <source data query>  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure>.COLUMN_VALUES (<mapped model columns>) <source data query>  
```  
  
## <a name="arguments"></a>引数  
 *model*  
 モデル識別子です。  
  
 *構造体*  
 構造識別子です。  
  
 *マップされたモデルの列*  
 列の識別子と入れ子になった識別子のコンマ区切りのリストです。  
  
 *ソース データ クエリ*  
 プロバイダー定義形式のソース クエリです。  
  
## <a name="remarks"></a>コメント  
 指定しない場合**マイニング モデルの**または**マイニング構造の**、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]名前に基づいてオブジェクトの種類を検索し、正しいオブジェクトを処理します。 サーバーが同じ名前のマイニング構造とマイニング モデルを持つ場合、エラーが返されます。  
  
 INSERT INTO、2 番目の構文形式を使用して *\<オブジェクト >* します。COLUMN_VALUES、データは、モデルを学習せず、モデルの列に直接挿入できます。 この方法によって、階層あるいは順序付けられた列を含むデータセットを使用する場合に便利な順序で、簡単に列データがモデルに提供されます。  
  
 使用する場合**INSERT INTO**マイニング モデルまたはマイニング構造とオフのままに、\<モデルの列をマップ > と\<ソース データ クエリ > ステートメントの動作の引数、 **ProcessDefault**、既に存在するバインドを使用します。 バインドが存在しない場合、ステートメントはエラーを返します。 詳細については**ProcessDefault**を参照してください[処理オプションと設定&#40;Analysis Services&#41;](../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)します。 次の例に構文を示します。  
  
```  
INSERT INTO [MINING MODEL] <model>  
```  
  
 指定した場合**マイニング モデルの**マップされた列とソース データ クエリ、モデルおよび関連付けられている構造の処理を提供します。  
  
 次の表は、オブジェクトの状態に依存する、異なる形式のステートメントの結果について示しています。  
  
|ステートメントから削除してください。|オブジェクトの状態|結果|  
|---------------|----------------------|------------|  
|マイニング モデルに挿入 *\<モデル >*|マイニング構造は処理されます。|マイニング モデルは処理されます。|  
||マイニング構造は処理されません。|マイニング モデルとマイニング構造は処理されます。|  
||マイニング構造に追加のマイニング モデルが含まれます。|処理は失敗します。 構造と関連するマイニング モデルを再処理する必要があります。|  
|マイニング構造に挿入 *\<構造体 >*|マイニング構造は処理されるか処理に失敗します。|マイニング構造と関連するマイニング モデルは処理されます。|  
|マイニング モデルに挿入 *\<モデル >* ソース クエリを含む<br /><br /> または<br /><br /> マイニング構造に挿入 *\<構造 >* ソース クエリを含む|構造またはモデルのどちらかが既に内容に含まれます。|処理は失敗します。 使用して、この操作を実行する前に、オブジェクトをクリアする必要があります[削除&#40;DMX&#41;](../dmx/delete-dmx.md)します。|  
  
## <a name="mapped-model-columns"></a>モデル列のマップ  
 使用して、\<モデルの列をマップする > 要素にマイニング モデル内の列のデータ ソースから列をマップすることができます。 \<モデルの列をマップする > 要素には、次の形式。  
  
```  
<column identifier> | SKIP | <table identifier> (<column identifier> | SKIP), ...  
```  
  
 使用して**スキップ**、ソース クエリに存在する必要がありますが、マイニング モデルに存在しない特定の列を除外することができます。 SKIP は、入力行セットに含まれる列を制御できない場合に役立ちます。 独自の OPENQUERY を記述する場合は、SKIP を使用するのではなく SELECT 列リストから列を除外することをお勧めします。  
  
 SKIP は、結合を実行するために入力行セットの列が必要だが、その列がマイニング構造では使用されない場合にも役立ちます。 この典型的な例が、入れ子になったテーブルを含むマイニング構造とマイニング モデルです。 この構造の入力行セットには、SHAPE 句を使用して階層的な行セットを作成するために使用される外部キー列が含まれますが、外部キー列がモデルで使用されることはほとんどありません。  
  
 SKIP の構文では、対応するマイニング構造列がない入力行セットの個々の列の位置に SKIP を挿入する必要があります。 たとえば、後述の入れ子になったテーブルの例では、APPEND 句で OrderNumber のクエリを実行して、結合を指定するために RELATE 句で使用できるようにする必要があります。ただし、マイニング構造では、入れ子になったテーブルに OrderNumber データを挿入しないようにする必要があります。 したがって、この例では、INSERT INTO 引数で OrderNumber ではなく SKIP キーワードを使用します。  
  
## <a name="source-data-query"></a>ソース データ クエリ  
 \<ソース データ クエリ > 要素は、次のデータ ソースの種類を含めることができます。  
  
-   **OPENQUERY**  
  
-   **OPENROWSET**  
  
-   **図形**  
  
-   すべて[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]行セットを返すクエリ  
  
 データ ソースの種類の詳細については、次を参照してください。 [&#60;ソース データ クエリ&#62;](../dmx/source-data-query.md)します。  
  
## <a name="basic-example"></a>基本の例  
 次の例では**OPENQUERY**で対象となるマイニング データに基づいて Naive Bayes モデルのトレーニングに、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベース。  
  
```  
INSERT INTO NBSample (CustomerKey, Gender, [Number Cars Owned],  
    [Bike Buyer])  
OPENQUERY([AdventureWorksDW2012],'Select CustomerKey, Gender, [NumberCarsOwned], [BikeBuyer]   
FROM [vTargetMail]')  
```  
  
## <a name="nested-table-example"></a>入れ子になったテーブルの例  
 次の例では**図形**を入れ子になったテーブルを含むアソシエーション マイニング モデルをトレーニングします。 最初の行が含まれたメモ**スキップ**代わりに、OrderNumber で必要な**SHAPE_APPEND**ステートメントではない、マイニング モデルで使用します。  
  
```  
INSERT INTO MyAssociationModel  
    ([OrderNumber],[Models] (SKIP, [Model])  
    )  
SHAPE {  
    OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
AS [Models]  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
