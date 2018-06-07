---
title: DRILLTHROUGH ステートメント (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f5b56c03ec6e575b647ed7eecaf26d35bfae047
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580064"
---
# <a name="mdx-data-manipulation---drillthrough"></a>MDX データ操作 - DRILLTHROUGH
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 任意の有効な多次元式 (MDX) 式の SELECT ステートメントです。  
  
 *Set_of_Attributes_and_Measures*  
 ディメンションの属性とメジャーのコンマ区切りのリストです。  
  
## <a name="remarks"></a>コメント  
 ドリルスルーとは、エンド ユーザーが詳細情報を取得するためにキューブから 1 つのセルを選択してそのセルのソース データから結果セットを取得する操作です。 既定では、ドリルスルーの結果セットは、選択したキューブ セルの値を計算するために評価されたテーブル行から導き出されます。 エンド ユーザーがドリルスルーを行う場合は、クライアント アプリケーションでこの機能がサポートされている必要があります。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、ROLAP パーティションまたはディメンションは、クエリを実行しない限り、MOLAP ストレージから直接、結果が取得されます。  
  
> [!IMPORTANT]  
>  ドリルスルーのセキュリティは、キューブで定義された全般的なセキュリティ オプションに基づいています。 ユーザーが MDX を使用して一部のデータを取得できない場合、そのユーザーはドリルスルーでも同様の制限を受けます。  
  
 対象のセルは、MDX ステートメントによって指定します。 指定された値、 **MAXROWS**引数は、結果の行セットによって返される行の最大数を示します。  
  
 既定では、返される最大行数は 10,000 行です。 つまり、このままにした場合**MAXROWS**指定しないと、表示される行数は 10,000 行以下です。 この値が小さすぎる、シナリオの場合は、設定**MAXROWS**数値は高いほどなど`MAXROWS 20000`です。 低すぎる全体的なである場合は、変更することで既定値を増やすことができます、 **olap \query\defaultdrillthroughmaxrows**サーバー プロパティです。 このプロパティの変更の詳細については、次を参照してください。 [Server Properties in Analysis Services](../analysis-services/server-properties/server-properties-in-analysis-services.md)です。  
  
 特に指定しない限り、返される列には、指定したメジャーのメジャー グループに関連するすべてのディメンション (多対多ディメンションを除く) に対応する粒度属性がすべて含められます。 ディメンションとメジャー グループを区別するために、キューブ ディメンションの先頭には $ が付いています。 **RETURN**句を使用して、ドリルスルー クエリで返される列を指定します。 次の関数が 1 つの属性に適用できるまたはによってメジャー、**RETURN**句。  
  
 Name(attribute_name)  
 指定された属性メンバーの名前を返します。  
  
 UniqueName(attribute_name)  
 指定された属性メンバーの一意名を返します。  
  
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
 次の例では、Australia の Reseller Sales Amount メジャー (既定のメジャー) に対応する 2007 年 7 月のセルを指定しています。 RETURN 句では、このセルの基になる各売上の日付、製品モデルの名前、従業員名、売上高、税額、および製品原価が返されるように指定しています。  
  
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
  
  
