---
title: (DMX) が存在する |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 99f6db275fcddaff3e739311ed588fb0ec776aaf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62506102"
---
# <a name="exists-dmx"></a>(DMX) が存在します。
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
 返します**true** 、サブクエリによって返される結果セットには少なくとも 1 つの行が含まれている場合を返しますそれ以外の場合、 **false**します。  
  
## <a name="remarks"></a>コメント  
 EXISTS の前にキーワード NOT を使用することができます。 たとえば、`WHERE NOT EXISTS (<subquery>)`します。  
  
 EXISTS のサブクエリの引数を追加する列の一覧が関連します。関数は、のみ条件を満たす行の存在を確認します。  
  
## <a name="examples"></a>使用例  
 EXISTS および NOT EXISTS を使用して、入れ子になったテーブルで条件をチェックすることができます。 これは、機能は、トレーニングやデータ マイニング モデルのテストに使用されるデータを制御するフィルターを作成するときに便利です。 詳細については、「[マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。  
  
 次の例がに基づいて、`[Association]`マイニング構造とマイニング モデルで作成した、 [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)します。 クエリでは、顧客が少なくとも 1 つの修正プログラムのキットを購入したケースのみを返します。  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 このクエリによって返されるのと同じデータを表示する別の方法は、アソシエーション ビューアーでモデルを開き、アイテム セットを右クリックする**Patch kit = Existing**を選択、**ドリル スルー**オプション、し選択**モデルの場合のみ**します。  
  
## <a name="see-also"></a>参照  
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [モデル フィルターの構文と例&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)  
  
  
