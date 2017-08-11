---
title: "RowNumber 関数 (レポート ビルダーおよび SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 25084e7140855c6535ef6432afdc09bee02a23e6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---rownumber-function"></a>レポートのビルダー関数、RowNumber 関数
  指定されたスコープの実行中の行数を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *スコープ (scope)*  
 (**String**) 行数を評価するコンテキストを示すデータセット、データ領域、またはグループの名前か、NULL (**では** Nothing [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) です。 **Nothing** は、最も外側のコンテキスト (通常はレポート データセット) を示します。  
  
## <a name="remarks"></a>解説  
 **RunningValue** では、集計関数の実行中の値が返されますが、 [RowNumber](../../reporting-services/report-design/report-builder-functions-runningvalue-function.md) では、指定したスコープ内の行数の実行中の値が返されます。 スコープを指定すると、行数を 1 にリセットするタイミングが指定されます。  
  
 *scope* には、式を指定することはできません。 *scope* には、コンテナー スコープを指定する必要があります。 一般的なスコープは、外側から内側の順に、レポート データセット、データ領域、行グループまたは列グループです。  
  
 列全体で値を増分するには、列グループの名前であるスコープを指定します。 行の下方向に向かって数を増分するには、行グループの名前であるスコープを指定します。  
  
> [!NOTE]  
>  行グループと列グループの両方を指定する複数の集計を含めた式はサポートされていません。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
## <a name="code-example"></a>コード例  
 Tablix データ領域の詳細行の **BackgroundColor** プロパティに使用できる式を次に示します。この式では、各グループの詳細行の色を交互に設定し、常に先頭が白になるようにしています。  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>参照  
 [レポート &#40; 内の式の使用レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式 &#40; 内のデータ型レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [式のスコープの合計、集計、および組み込みコレクション & #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
