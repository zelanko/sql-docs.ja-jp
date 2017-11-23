---
title: "MDX データ定義ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- data definition statements [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 1f975d7f-8875-43b6-a571-9d5cd7c70217
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 32371f26e6c4cef2398d505d603dcbca6505a846
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition-statements-mdx"></a>MDX データ定義ステートメント (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  多次元式 (MDX) では、データ定義ステートメントを使用して、多次元オブジェクトの作成、削除、操作を行います。 次の表に、使用可能なデータ定義ステートメントを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[ALTER CUBE ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-alter-cube.md)|指定されたキューブの構造を変更します。|  
|[ACTION ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-action.md)|アクションを作成します。アクションは、キューブ、ディメンション、階層、下位オブジェクトに関連付けることができます。|  
|[CELL CALCULATION ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-cell-calculation.md)|キューブ内で指定されている組のセットに対して MDX 式を評価する計算を作成します。|  
|[GLOBAL CUBE ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-global-cube.md)|サーバーのキューブのサブキューブを基にして、ローカルに保存されるキューブを作成します。 ローカルに保存されるキューブに接続する場合、サーバーに接続する必要はありません。|  
|[MEMBER ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-member.md)|計算されるメンバーを作成します。|  
|[SESSION CUBE ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-session-cube.md)|サーバーのキューブを基にして、同じセッション内のすべてのクエリで使用できるキューブを作成し、データを設定します。|  
|[SET ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-set.md)|指定されたキューブの名前付きセットを作成します。|  
|[SUBCUBE ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-subcube.md)|指定されたキューブまたはサブキューブのキューブ空間を指定されたサブキューブに再定義します。|  
|[DROP ACTION ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-drop-action.md)|指定されたキューブから指定されたアクションを削除します。|  
|[DROP CELL CALCULATION ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-drop-cell-calculation.md)|指定されたセル計算を削除します。|  
|[DROP MEMBER ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-drop-member.md)|計算されるメンバーを削除します。|  
|[DROP SET ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-drop-set.md)|名前付きセットを削除します。|  
|[DROP SUBCUBE ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-drop-subcube.md)|指定されたサブキューブを削除し、指定された名前の以前のキューブ定義またはサブキューブ定義に戻します。|  
|[更新の CUBE ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-refresh-cube.md)|キューブのクライアント キャッシュを更新します。|  
  
## <a name="see-also"></a>参照  
 [MDX ステートメント リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-statement-reference-mdx.md)   
 [MDX データ操作ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [MDX スクリプト ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-scripting-statements-mdx.md)  
  
  
