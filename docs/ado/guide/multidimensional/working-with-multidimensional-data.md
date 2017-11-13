---
title: "多次元データを扱う |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multidimensional data [ADO]
ms.assetid: 84387746-aa3e-44fd-ad6c-a8214a6966dc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e14c59fd0620129486408d33339e80624743f02
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="working-with-multidimensional-data"></a>多次元データの操作
A*セルセット*多次元データに対するクエリの結果を示します。 軸、通常は 4 つ以下の軸と通常 2 つまたは 3 つのコレクションで構成されます。 *軸*探すか、キューブ内の特定の値をフィルター処理に使用される 1 つまたは複数のディメンションのメンバーのコレクションです。  
  
 A*位置*軸に沿ったポイントです。 1 つのディメンションで構成される軸、それらの位置は、ディメンションのメンバーのサブセットです。 軸は、1 つ以上のディメンションで構成される場合は、各位置が、複合エンティティ *n*  where 部分 *n* その軸に沿って配置ディメンションの数です。 位置の各部分は、1 つの構成要素であるディメンションのメンバーです。  
  
 たとえば場合は、売上データを含むキューブからディメンションの Geography と製品ディメンションは、セルセットの x 軸に沿った指向は、この軸に沿った位置可能性がありますメンバーを含む"USA"と「コンピューター」 この例では、x 軸に沿った位置を決定する必要があります各ディメンションのメンバーは、軸に沿った並びます。  
  
 A*セル*軸座標の交点にあるオブジェクトです。 各セルには、データ自体、書式設定された文字列 (セル データの表示可能な項目のフォーム)、およびセルの序数値を含むに関連付けられている情報の複数の部分です。 (各セルは、セルセットの一意の序数値です。 セルセット内の最初のセルの序数値は 0、8 つの列を含むセル セットの 2 番目の行の左端のセルに 8 個の序数値は中です。)  
  
 次の 6 つのディメンションをキューブがあるなど、(このキューブ スキーマわずかに異なるで指定された例では、注意してください[マルチ ディメンション スキーマの概要とデータ](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md))。  
  
-   販売員  
  
-   Geography (自然階層): 大陸、国、状態、およびなど  
  
-   四半期-四半期、月、日  
  
-   Years  
  
-   メジャー、売上、PercentChange、BudgetedSales  
  
-   Products  
  
 次のセル セットでは、1991 すべての製品の売上を表します。  
  
> [!NOTE]
>  セルの値の例では、軸の位置の序数が最初の桁が x 軸の位置と y 軸の位置 2 番目の数字を表すの順序付けされたペアとして見なすことができます。  
  
 このセル セットの特性は次のとおりです。  
  
-   軸ディメンション: 四半期、販売員、Geography  
  
-   ディメンションをフィルター処理: メジャー、年、製品  
  
-   2 つの軸: (x、または軸 0) の列と行 (y または軸 1)  
  
-   x 軸: 入れ子になった 2 つの販売員と Geography ディメンションは、  
  
-   y 軸: 四半期のディメンション  
  
 X 軸が 2 つの入れ子になったディメンション: 販売員および地域。 Geography から次の 4 つのメンバーが選択されて: シアトル、ボストン、米国南部、および日本します。 営業担当者から 2 つのメンバーが選択されて: バレンタインと Nash です。 これには、この軸 (8 = 4 * 2) 8 つの位置の合計が生成されます。  
  
 各座標は、2 つのメンバーの位置として表されます。 — Geography ディメンションから別の販売員のディメンションと 1 つ。  
  
```  
(Valentine, Seattle), (Valentine, Boston), (Valentine, USA_North),  
(Valentine, Japan), (Nash, Seattle), (Nash, Boston), (Nash, USA_North),  
(Nash, Japan)  
```  
  
 Y 軸には、次の 8 つの位置を含む 1 つだけのディメンションがあります。  
  
```  
Jan, Feb, Mar, Qtr2, Qtr3, Oct, Nov, Dec  
```  
  
 セル セット、セル、軸、および位置はすべてによって表される ADO MD で対応するオブジェクト:[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)、[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)、[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)、および[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md).  
  
## <a name="see-also"></a>参照  
 [ADO MD オブジェクト モデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (多次元) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [マルチ ディメンション スキーマとデータの概要](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [ADO MD を使用したプログラミング](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [ADO MD と ADO の併用](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)

