---
title: DRILLTHROUGH ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82dd8a9527b85350cae31396ad4d238ef1c8c850
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187655"
---
# <a name="mdx-data-manipulation---drillthrough"></a>MDX データ操作 - DRILLTHROUGH


  キューブ内の指定されたセルの作成に使用されたテーブル行を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DRILLTHROUGH[MAXROWSUnsigned_Integer]   
      <MDX SELECT statement>   
      [RETURNSet_of_Attributes_and_Measures   
            [,Set_of_Attributes_and_Measures ...]  
      ]  
```  
  
## <a name="arguments"></a>引数  
 *Unsigned_Integer*  
 正の整数値です。  
  
 *MDX SELECT statement*  
 有効な多次元式 (MDX) 式 SELECT ステートメント。  
  
 *Set_of_Attributes_and_Measures*  
 ディメンション属性およびメジャーのコンマ区切りの一覧。  
  
## <a name="remarks"></a>コメント  
 ドリルスルーは、エンドユーザーがキューブからの 1 つのセルの選択をそのセルのソース データからより詳細な情報を取得するために結果セットを取得する操作。 既定では、ドリルスルーの結果セットは、選択したキューブ セルの値を計算するために評価されたテーブル行から導き出されます。 エンドユーザーにドリルスルーするには、クライアント アプリケーションはこの機能をサポートする必要があります。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、ROLAP パーティションまたはディメンションがクエリを実行しない限り、MOLAP ストレージから直接、結果が取得されます。  
  
> [!IMPORTANT]  
>  ドリルスルーのセキュリティは、キューブで定義された全般的なセキュリティ オプションに基づいています。 場合は、ユーザーは、MDX を使用してデータを取得することはできません、ドリルスルーは内のユーザーを制限も、まったく同じ方法です。  
  
 対象のセルは、MDX ステートメントによって指定します。 によって指定された値、 **MAXROWS**引数を結果の行セットによって返される行の最大数を示します。  
  
 既定では、返される行の最大数は 10,000 行です。 つまりのままにする場合**MAXROWS**指定しないと、10,000 行が取得されます以下です。 この値が小さすぎる、シナリオの場合は設定できます**MAXROWS**数値は高いほどなど`MAXROWS 20000`します。 小さすぎる場合全体的に見て、変更することで、既定値を増やすことができます、 **olap \query\defaultdrillthroughmaxrows**サーバー プロパティ。 このプロパティを変更する方法についての詳細については、次を参照してください。 [Server Properties in Analysis Services](../analysis-services/server-properties/server-properties-in-analysis-services.md)します。  
  
 指定しない場合、返される列には、多対多ディメンション以外の指定したメジャーのメジャー グループに関連するすべてのディメンションの粒度属性にはすべてが含まれます。 キューブ ディメンションの後に、ディメンションとメジャー グループを区別するために $ が付いています。 **RETURN**句を使用して、ドリルスルー クエリで返される列を指定します。 次の関数が 1 つの属性に適用できるまたはによってメジャー、**RETURN**句。  
  
 Name(attribute_name)  
 指定された属性メンバーの名前を返します。  
  
 UniqueName(attribute_name)  
 指定された属性メンバーの一意の名前を返します。  
  
 Key(attribute_name[, N])  
 指定された属性メンバーのキーを返します。N は、複合キーの列 (存在する場合) を指定します。 N の既定値は 1 です。  
  
 Caption(attribute_name)  
 指定された属性メンバーのキャプションを返します。  
  
 MemberValue(attribute_name)  
 指定された属性メンバーのメンバー値を返します。  
  
 CustomRollup(attribute_name)  
 指定された属性メンバーのカスタム ロールアップ式を返します。  
  
 CustomRollupProperties(attribute_name)  
 指定された属性メンバーのカスタム ロールアップ プロパティを返します。  
  
 UnaryOperator(attribute_name)  
 指定された属性メンバーの単項演算子を返します。  
  
## <a name="example"></a>例  
 次の例は、reseller sales amount メジャー (既定のメジャー) 国オーストラリアの 2007 年 7 月の 1 か月のセルを指定します。 RETURN 句では、各販売、製品モデルの名前、従業員の名前、日付の売り上げ高、税額、および製品のコストは、このセルの基になる値を返すことを指定します。  
  
```  
DRILLTHROUGH  
SELECT  
   ([Date].[Calendar].[Month].[July 2007])  
ON 0   
FROM [Adventure Works]  
WHERE [Geography].[Country].[Australia]  
RETURN   
  [$Date].[Date]  
  ,KEY([$Product].[Model Name])  
  ,NAME([$Employee].[Employee])  
  ,[Reseller Sales].[Reseller Sales Amount]  
  ,[Reseller Sales].[Reseller Tax Amount]  
  ,[Reseller Sales].[Reseller Standard Product Cost]  
```  
  
## <a name="see-also"></a>参照  
 [MDX データ操作ステートメント&#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
