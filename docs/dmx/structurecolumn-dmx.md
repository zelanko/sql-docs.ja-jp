---
title: "StructureColumn (DMX) |Microsoft ドキュメント"
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
f1_keywords:
- StructureColumn
dev_langs:
- DMX
helpviewer_keywords:
- StructureColumn function
ms.assetid: 57557536-4bfa-4fa7-bf7a-fb8722ca200d
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3e7f727e1007c6502e6612ccef563f670837cf5c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="structurecolumn-dmx"></a>StructureColumn (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したケースに対応する構造列の値、または指定したケースの入れ子になったテーブルのテーブル値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StructureColumn('structure column name')  
```  
  
## <a name="arguments"></a>引数  
 structure-column-name。  
 ケースまたは入れ子になったテーブルのマイニング構造列の名前。  
  
## <a name="result-type"></a>結果の種類  
 返される型で参照されている列の型によって異なります、\<構造の列名 > のパラメーターです。 たとえば、参照されるマイニング構造列がスカラー値を含む場合、関数はスカラー値を返します。  
  
 参照されるマイニング構造列が入れ子になったテーブルである場合、関数はテーブル値を返します。 返されたテーブル値は、サブ SELECT ステートメントの FROM 句に使用できます。  
  
## <a name="remarks"></a>解説  
 この関数はポリモーフィックで、SELECT 式リスト、WHERE 条件式、ORDER BY 式など、式を使用できるステートメント内の任意の場所で使用できます。  
  
 マイニング構造内の列の名前は文字列値でありそのため、単一引用符で囲む必要があります。 たとえば、 `StructureColumn('`**列 1**`')`です。 同じ名前を持つ列が複数ある場合、名前は SELECT ステートメントが含まれるコンテキスト内で解決されます。  
  
 使用してクエリから返された結果、 **StructureColumn**関数は、モデルに対するフィルターの存在を受けます。 つまり、モデル フィルターは、マイニング モデルに含まれるケースを制御します。 したがって、構造列上のクエリは、マイニング モデルに使用されたケースのみを返します。 ケース テーブルと入れ子になったテーブルの両方に対するマイニング モデル フィルターの影響を示すコード例については、このトピックの「例」のセクションを参照してください。  
  
 DMX SELECT ステートメントでこの関数を使用する方法の詳細については、次を参照してください。 [SELECT FROM &#60; モデル &#62;。場合 (&) #40";"DMX"&"#41;](../dmx/select-from-model-cases-dmx.md)または[SELECT FROM &#60; 構造 &#62;。ケース](../dmx/select-from-structure-cases.md)です。  
  
## <a name="error-messages"></a>エラー メッセージ  
 次のセキュリティ エラーは、親のマイニング構造に対するドリルスルー権限がユーザーに与えられていない場合に発生します。  
  
 '%{user/}' ユーザーには、'%{model/}' マイニング モデルの親マイニング構造にドリルスルーする権限がありません。  
  
 次のエラー メッセージは、無効な構造列名が指定された場合に表示されます。  
  
 '%{structure-column-name/}' マイニング構造列が '%{structure/}' 親マイニング構造内に見つかりませんでした (現在のコンテキスト (line %{line/}、列 %{column/}))。  
  
## <a name="examples"></a>使用例  
 ここに示す例では、次のマイニング構造を使用します。 マイニング構造に 2 つの入れ子になったテーブル列が含まれているメモ`Products`と`Hobbies`です。 `Hobbies` 列の入れ子になったテーブルには、入れ子になったテーブルのキーとして使用される単一列があります。 入れ子になったテーブルで、`Products`列は、複雑な入れ子になったテーブル キー列と入力に使用されるその他の列の両方があります。 次の例は、モデルですべての列を使用しない可能性があっても、多くの異なる列を組み込んでデータ マイニング構造を設計する方法を示しています。 これらの列の一部は、モデル レベルでパターンの汎用化に役立たない可能性がありますが、ドリルスルーには非常に有効です。  
  
```  
CREATE MINING STRUCTURE [MyStructure]   
(  
CustomerName TEXT KEY,  
Occupation TEXT DISCRETE,  
Age LONG CONTINUOUS,  
MaritalStatus TEXT DISCRETE,  
Income LONG CONTINUOUS,  
Products  TABLE  
 (  
    ProductNameTEXT KEY,  
    Quantity LONG CONTINUOUS,  
    OnSale BOOLEAN  DISCRETE  
)  
 Hobbies  TABLE  
 (  
    Hobby KEY  
 ))  
```  
  
 次に、以下のコード例で、作成した構造に基づいてマイニング モデルを作成します。  
  
```  
ALTER MINING STRUCTURE [MyStructure] ADD MINING MODEL [MyModel] (  
CustomerName,  
Age,  
MaritalStatus,  
Income PREDICT,  
Products   
(  
ProductName  
) WITH FILTER(NOT OnSale)  
) USING Microsoft_Decision_Trees   
WITH FILTER(EXISTS (Products))  
```  
  
### <a name="sample-query-1-returning-a-column-from-the-mining-structure"></a>サンプル クエリ 1: マイニング構造から列を返す  
 次のサンプル クエリでは、マイニング モデルの一部として定義されている列 `CustomerName` および `Age` が返されます。 ただし、このクエリでは、構造の一部であってもマイニング モデルの一部ではない `Age` 列も返されます。  
  
```  
SELECT CustomerName, Age, StructureColumn(‘Occupation’) FROM MyModel.CASES   
WHERE Age > 30  
```  
  
 年齢が 30 歳を超える顧客にケースを制限する行のフィルター処理は、モデルのレベルで実行されます。 したがって、この式は、構造データに含まれているが、モデルから使用されないケースを返しません。 フィルター条件は、モデルの作成に使用されるため (`EXISTS (Products)`) ケースを制限する製品を購入した顧客のみ、ある可能性があります構造内のこのクエリによって返されないケースです。  
  
### <a name="sample-query-2-applying-a-filter-to-the-structure-column"></a>サンプル クエリ 2: 構造列にフィルターを適用する  
 次のサンプル クエリは、モデルの列を返すだけでなく`CustomerName`と`Age`、テーブルと入れ子になったテーブル`Products`も、列の値を返しますが、`Quantity`入れ子になったテーブルではないモデルの一部です。  
  
```  
SELECT CustomerName, Age,  
(SELECT ProductName, StructureColumn(‘Quantity’) FROM Products) FROM MA.CASES   
WHERE StructureColumn(‘Occupation’) = ‘Architect’  
```  
  
 この例では、フィルターが適用は、職業が Architect 顧客にケースを制限する構造の列に注意してください (`WHERE StructureColumn(‘Occupation’) = ‘Architect’`)。 モデル フィルターの条件がケースに適用されるは、モデルの作成時に常に、ためには、少なくとも 1 つの条件を満たすケースのみ行が、`Products`テーブルがモデルのケースに含まれています。 したがって、両方のフィルターを入れ子になったテーブル`Products`とケース フィルター`(‘Occupation’)`適用されます。  
  
### <a name="sample-query-3-selecting-columns-from-a-nested-table"></a>サンプル クエリ 3: 入れ子になったテーブルから列を選択する  
 次のサンプル クエリでは、トレーニング ケースとして使用された顧客の名前がモデルから返されます。 顧客ごとに、購入の詳細を含む入れ子になったテーブルも返されます。 モデルに含まれていますが、`ProductName`列、モデルの値を使用していない、`ProductName`列です。 モデルだけが確認では、通常、製品を購入したかどうか (`NOT``OnSale`) 価格。 このクエリでは、製品名だけでなく、モデルには含まれていない購入した数量も返されます。  
  
```  
SELECT CustomerName,    
(SELECT ProductName, StructureColumn('Quantity')FROM Products)   
FROM MyModel.CASES  
```  
  
 マイニング モデルでドリルスルーが有効でない限り、`ProductName` 列または `Quantity` 列を返すことはできません。  
  
### <a name="sample-query-4-filtering-on-and-returning-nested-table-columns"></a>サンプル クエリ 4: フィルターを適用して入れ子になったテーブル列を返す  
 次のサンプル クエリは、マイニング構造に含まれるがモデルに含まれない、ケースおよび入れ子になったテーブル列を返します。 モデルは既に `OnSale` 製品が存在するかどうかでフィルター処理されていますが、このクエリはマイニング構造列 `Quantity` にフィルターを追加します。  
  
```  
SELECT CustomerName, Age, StructureColumn('Occupation'),   
(SELECT ProductName, StructureColumn('Quantity') FROM Products)   
FROM MyModel.CASES   
WHERE EXISTS (SELECT * FROM Products WHERE StructureColumn('Quantity')>1)  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

