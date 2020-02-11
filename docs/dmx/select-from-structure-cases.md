---
title: '[構造&lt;&gt;から] を選択します。ケース |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 041d6ade2363b4a33528bd44438a2fcb440d61ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928295"
---
# <a name="select-from-ltstructuregtcases"></a>[構造&lt;&gt;から] を選択します。場合
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング構造の作成に使用されたケースを返します。  
  
 ドリルスルーが構造で使用可能でない場合、ステートメントは失敗します。 また、マイニング構造に対するドリルスルー権限がユーザーに与えられていない場合、ステートメントは失敗します。  
  
 で[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は、新しいマイニング構造のドリルスルーが既定で有効になっています。 特定の構造に対してドリルスルーが有効になっているかどうかを確認するには、 **Cachemode**プロパティの値が**KeepTrainingCases**に設定されているかどうかを確認します。  
  
 **Cachemode**の値が**clearafterprocessing**に変更された場合、構造ケースはキャッシュから消去され、ドリルスルーを使用することはできません。  
  
> [!NOTE]  
>  データマイニング拡張機能 (DMX) を使用して、マイニング構造のドリルスルーを有効または無効にすることはできません。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [TOP n] <expression list> FROM <structure>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 省略可能。 返す行数を指定する整数値です。  
  
 *式の一覧*  
 式のコンマ区切りのリストです。  
  
 式には、列識別子、ユーザー定義関数、および VBA 関数を含めることができます。  
  
 *データ*  
 構造体の名前。  
  
 *条件式*  
 列リストから返される値を制限する条件。  
  
 *条件*  
 省略可能。 スカラー値を返す式。  
  
## <a name="remarks"></a>解説  
 モデルと構造の両方でドリルスルーが有効になっている場合、マイニング構造およびモデルに対するドリルスルー権限を持つロールのメンバーは、モデルに含まれていない構造列を返すことができます。そのためには、次の構文を使用します。  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 したがって、機密データや個人情報を保護するには、個人情報をマスクするデータソースビューを構築し、マイニング構造またはマイニングモデルに対して**Allowdrillthrough スルー**権限を必要な場合にのみ許可する必要があります。  
  
## <a name="examples"></a>例  
 次の例は、マイニング構造、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]データベースに基づく対象メーリング、および関連するマイニングモデルに基づいています。 詳細については、「[基本的なデータマイニングチュートリアル](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」を参照してください。  
  
### <a name="example-1-drill-through-to-structure-cases"></a>例 1: 構造ケースにドリルスルーする  
 次の例では、マイニング構造内の最も古い500の顧客の一覧を返します (対象メーリング)。 このクエリでは、マイニングモデル内のすべての列が返されますが、行は自転車を購入したユーザーに限定され、年齢別に並べ替えられます。 必要な列のみを返すように式のリストを編集することもできます。  
  
```  
SELECT TOP 500 *  
FROM [Targeted Mailing].Cases  
WHERE [Bike Buyer] = 1  
ORDER BY Age DESC;  
```  
  
### <a name="example-2-drillthrough-to-test-or-training-cases-only"></a>例 2: テストケースまたはトレーニングケースへのドリルスルーのみ  
 次の例では、テスト用に予約されている対象メーリングの構造ケースの一覧を返します。 提示されたテストセットがマイニング構造に含まれていない場合、既定ではすべてのケースがトレーニングケースとして扱われ、このクエリは0ケースを返します。  
  
```  
SELECT [Customer Key], Gender, Age  
FROM [Targeted Mailing].Cases  
WHERE IsTestCase();  
```  
  
 トレーニングケースを返すには、関数`IsTrainingCase()`を置き換えます。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;を選択 &#40;](../dmx/select-dmx.md)   
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
