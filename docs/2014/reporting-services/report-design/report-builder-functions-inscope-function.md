---
title: InScope 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e677c9e02f452a486b9168f15c662362640ea86e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174409"
---
# <a name="inscope-function-report-builder-and-ssrs"></a>InScope 関数 (レポート ビルダーおよび SSRS)
  アイテムの現在のインスタンスが、指定したスコープ内にあるかどうかを示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *スコープ (scope)*  
 (`String`) データセット、データ領域またはスコープを指定するグループの名前。  
  
## <a name="return-type"></a>戻り値の型  
 返します、`Boolean`です。  
  
## <a name="remarks"></a>コメント  
 `InScope`関数で指定されたスコープ内のメンバーシップ用のスコープ レポート アイテムの現在のインスタンスのテスト、*スコープ*パラメーター。  
  
 *Scope* には、式を指定することはできません。  
  
 一般的な使用、`InScope`関数はデータ領域を持つ動的でスコープ設定されます。 たとえば、`InScope`セットを指定する別のレポート名と異なるに応じてどのセルがクリックされたパラメーターのデータ領域のセル内のドリルスルー リンクで使用できます。 この例を以下に示します。  
  
-   次の式では、ドリルスルー リンクのレポート名として使用し、 `ProductDetail` グループ内のセルがクリックされた場合は `Month` レポートが開き、それ以外のセルがクリックされた場合は `ProductSummary` レポートが開くようにしています。  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   次の式で使用される、 `Omit` 、詳細レポート パラメーターのプロパティ パラメーターが渡されるターゲット レポートにセルがクリックされたのであれば、`Product`グループ。  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、アイテムの現在のインスタンスが、 `Product` データセット、データ領域、またはグループのスコープにあるかどうかが示されます。  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>参照  
 [レポートで式を使用して&#40;レポート ビルダーおよび SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [式の合計、集計、および組み込みコレクションのスコープ&#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  