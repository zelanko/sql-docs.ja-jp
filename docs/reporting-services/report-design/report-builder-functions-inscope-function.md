---
title: "InScope 関数 (レポート ビルダーおよび SSRS) |Microsoft ドキュメント"
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
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d8dacf74335cafa2585168288ea88d316b23d037
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---inscope-function"></a>レポートのビルダー関数 - InScope 関数
  アイテムの現在のインスタンスが、指定したスコープ内にあるかどうかを示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *スコープ (scope)*  
 (**String**) スコープを指定するデータセット、データ領域、またはグループの名前です。  
  
## <a name="return-type"></a>戻り値の型  
 **Boolean**値を返します。  
  
## <a name="remarks"></a>解説  
 **InScope** 関数では、レポート アイテムの現在のインスタンスのスコープを調べて、 *scope*パラメーターで指定されたスコープのメンバーシップを確認します。  
  
 *Scope* には、式を指定することはできません。  
  
 **InScope** 関数は、通常、動的スコープを利用するデータ領域で使用されます。 たとえば、 **InScope** をデータ領域のセル内のドリルスルー リンクに使用して、クリックされたセルに応じて異なるレポート名とパラメーター セットが返されるようにすることができます。 この例を以下に示します。  
  
-   次の式では、ドリルスルー リンクのレポート名として使用し、 `ProductDetail` グループ内のセルがクリックされた場合は `Month` レポートが開き、それ以外のセルがクリックされた場合は `ProductSummary` レポートが開くようにしています。  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   次の式では、詳細レポート パラメーターの **Omit** プロパティに使用し、 `Product` グループ内のセルがクリックされた場合のみ、目的のレポートにパラメーターが渡されるようにしています。  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、アイテムの現在のインスタンスが、 `Product` データセット、データ領域、またはグループのスコープにあるかどうかが示されます。  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>参照  
 [レポート &#40; 内の式の使用レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式 &#40; 内のデータ型レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [式のスコープの合計、集計、および組み込みコレクション & #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
