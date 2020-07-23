---
title: 存在 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fdf58a943986dc43f82ef7023b68a2c6168a5518
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971717"
---
# <a name="exists-dmx"></a>存在 (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  指定されたサブクエリが少なくとも1つの行を返す場合に**true**を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>引数  
 *subquery*  
 Select * FROM [WHERE] 形式の SELECT ステートメント \<column name> \<predicate list> 。  
  
## <a name="result-type"></a>結果の種類  
 サブクエリによって返される結果セットに少なくとも1つの行が含まれている場合に**true**を返します。それ以外の場合は**false**を返します。  
  
## <a name="remarks"></a>注釈  
 EXISTS の前に NOT キーワードを使用できます。たとえば、のように `WHERE NOT EXISTS (<subquery>)` なります。  
  
 EXISTS のサブクエリ引数に追加する列の一覧は、関係ありません。関数は、条件を満たす行が存在するかどうかのみをチェックします。  
  
## <a name="examples"></a>例  
 EXISTS と NOT EXISTS を使用して、入れ子になったテーブルの条件を確認することができます。 これは、データマイニングモデルのトレーニングまたはテストに使用されるデータを制御するフィルターを作成する場合に便利です。 詳細については、「[マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining)」を参照してください。  
  
 次の例は、 `[Association]` 「[基本的なデータマイニングチュートリアル](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」で作成したマイニング構造とマイニングモデルに基づいています。 このクエリでは、顧客が少なくとも1つの patch kit を購入したケースのみが返されます。  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 このクエリによって返される同じデータを表示する別の方法として、アソシエーションビューアーでモデルを開き、[アイテム**セット Patch kit = Existing**] を右クリックし**て [ドリルスルー** ] オプションを選択し、[**モデルケースのみ**] を選択します。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [モデル フィルターの構文と例 (Analysis Services - データ マイニング)](https://docs.microsoft.com/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining)  
  
  
