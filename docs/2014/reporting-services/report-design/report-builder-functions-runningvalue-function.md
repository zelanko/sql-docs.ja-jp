---
title: RunningValue 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: fce2675b361b3b6d4d8ffc46afdabb0b6d128cc7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180862"
---
# <a name="runningvalue-function-report-builder-and-ssrs"></a>RunningValue 関数 (レポート ビルダーおよび SSRS)
  式で指定された NULL 以外のすべての数値の実行中の集計を、指定されたスコープに対して評価して返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *式 (expression)*  
 この集計関数の実行対象の式です ( `[Quantity]`など)。  
  
 *function*  
 (`Enum`)、式に適用する集計関数の名前`Sum`します。 この関数にすることはできません`RunningValue`、 `RowNumber`、または`Aggregate`します。  
  
 *スコープ (scope)*  
 (`String`) 集計を評価するコンテキストを示すデータセット、データ領域、またはグループの名前である文字列定数か、NULL ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) です。 `Nothing` 最も外側のコンテキストでは、通常は、レポート データセットを指定します。  
  
## <a name="return-type"></a>戻り値の型  
 *function* パラメーターに指定された集計関数によって決まります。  
  
## <a name="remarks"></a>コメント  
 値は、`RunningValue`スコープの新しいインスタンスごとの場合は 0 にリセットされます。 グループが指定された場合は、累計値はグループ式の変更時にリセットされます。 データ領域が指定された場合は、累計値はデータ領域の新しいインスタンスごとにリセットされます。 データセットが指定された場合は、累計値はデータセット全体にわたってリセットされません。  
  
 `RunningValue` は、フィルター式または並べ替え式では使用できません。  
  
 実行中の値が計算される一連のデータは、同じデータ型である必要があります。 同じデータ型に複数の数値データ型を持つデータを変換するなどの変換関数を使用して、 `CInt`、`CDbl`または`CDec`します。 詳細については、「 [データ型変換関数](http://go.microsoft.com/fwlink/?LinkId=96142)」を参照してください。  
  
 *Scope* には、式を指定することはできません。  
  
 *Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。  
  
-   入れ子集計のスコープは、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。 式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。  
  
-   入れ子集計のスコープには、データセット名は使用できません。  
  
-   *式*する必要がありますが含まれていない`First`、 `Last`、 `Previous`、または`RunningValue`関数。  
  
-   *Expression* には、 *recursive*を指定する入れ子集計を含めることができません。  
  
 行数の累計値を計算するには、`RowNumber` を使用します。 詳細については、「[RowNumber 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-rownumber-function.md)」を参照してください。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
 再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次のコード例では、最も外側のスコープ (データセット) の `Cost` フィールドの累計が返されます。  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 次のコード例では、 `Score` データセットの `DataSet1`フィールドの累計が返されます。  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 次のコード例では、最も外側のスコープの `Traffic Charges` フィールドの累計が返されます。  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## <a name="see-also"></a>参照  
 [レポートで式を使用して&#40;レポート ビルダーおよび SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ&#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
