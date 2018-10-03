---
title: RowNumber 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: abf8cdd0eb4ffceb21061ea0101a42e4b84f3773
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105712"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a>RowNumber 関数 (レポート ビルダーおよび SSRS)
  指定されたスコープの実行中の行数を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *スコープ (scope)*  
 (`String`) データセット、データ領域、またはグループ、または null の名前 (`Nothing`で[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)])、行の数を評価するコンテキストを指定します。 `Nothing` 最も外側のコンテキストでは、通常は、レポート データセットを指定します。  
  
## <a name="remarks"></a>コメント  
 `RowNumber` 同様に、指定したスコープ内の行のカウントの実行中の値を返します[RunningValue](report-builder-functions-runningvalue-function.md)集計関数の実行中の値を返します。 スコープを指定すると、行数を 1 にリセットするタイミングが指定されます。  
  
 *scope* には、式を指定することはできません。 *scope* には、コンテナー スコープを指定する必要があります。 一般的なスコープは、外側から内側の順に、レポート データセット、データ領域、行グループまたは列グループです。  
  
 列全体で値を増分するには、列グループの名前であるスコープを指定します。 行の下方向に向かって数を増分するには、行グループの名前であるスコープを指定します。  
  
> [!NOTE]  
>  行グループと列グループの両方を指定する複数の集計を含めた式はサポートされていません。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
## <a name="code-example"></a>コード例  
 使用できる式を次に、`BackgroundColor`常に先頭が白、各グループの詳細行の色を交互に Tablix データ領域の詳細行のプロパティ。  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>参照  
 [レポートで式を使用して&#40;レポート ビルダーおよび SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ&#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
