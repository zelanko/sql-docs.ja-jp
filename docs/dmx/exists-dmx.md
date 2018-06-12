---
title: (DMX) が存在する |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 936612dba4f466c5bc78f20f5a3ea07954a20a1c
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843025"
---
# <a name="exists-dmx"></a>Exists (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  返します**true**場合は、指定されたサブクエリが少なくとも 1 つの行を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>引数  
 *subquery*  
 フォームの選択の SELECT ステートメント * FROM\<列名 > [場所\<述語の一覧 >] です。  
  
## <a name="result-type"></a>結果の種類  
 返します**true** 、サブクエリによって返される結果セットに少なくとも 1 つの行が含まれている場合を返しますそれ以外の場合、 **false**です。  
  
## <a name="remarks"></a>コメント  
 EXISTS の前にキーワード NOT を使用することができます。 たとえば、`WHERE NOT EXISTS (<subquery>)`です。  
  
 EXISTS のサブクエリの引数に追加する列の一覧は関係ありません。関数は条件に一致する行が存在するかどうかのみをチェックします。  
  
## <a name="examples"></a>使用例  
 入れ子になったテーブル内の条件のチェックに EXISTS および NOT EXISTS を使用できます。 これは、データ マイニング モデルのトレーニングやテストに使用するデータを制御するフィルターを作成する場合に役立ちます。 詳細については、「[マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。  
  
 次の例がに基づいて、`[Association]`マイニング構造とマイニング モデルで作成した、[基本的なデータ マイニング チュートリアル」](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。 このクエリでは、顧客が Patch Kit を少なくとも 1 つ購入したケースのみを返します。  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 このクエリによって返される同じデータを表示する別の方法は、アソシエーション ビューアーでモデルを開き、アイテム セットを右クリックする**Patch kit = Existing**を選択、**ドリル スルー**オプションをクリックし **モデルの場合のみ**です。  
  
## <a name="see-also"></a>参照  
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [モデル フィルターの構文と例&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)  
  
  
