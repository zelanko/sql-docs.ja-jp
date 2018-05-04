---
title: MDX データ定義ステートメント (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- data definition statements [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 1f975d7f-8875-43b6-a571-9d5cd7c70217
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 84a173a4e3496d61f8f1b1fc837908d2706af5b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition-statements-mdx"></a>MDX データ定義ステートメント (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) では、データ定義ステートメントを使用して、多次元オブジェクトの作成、削除、操作を行います。 次の表に、使用可能なデータ定義ステートメントを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[ALTER CUBE ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-alter-cube.md)|指定されたキューブの構造を変更します。|  
|[CREATE ACTION ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-action.md)|アクションを作成します。アクションは、キューブ、ディメンション、階層、下位オブジェクトに関連付けることができます。|  
|[CELL CALCULATION ステートメント & #40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-cell-calculation.md)|キューブ内で指定されている組のセットに対して MDX 式を評価する計算を作成します。|  
|[CREATE GLOBAL CUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-global-cube.md)|サーバーのキューブのサブキューブを基にして、ローカルに保存されるキューブを作成します。 ローカルに保存されるキューブに接続する場合、サーバーに接続する必要はありません。|  
|[MEMBER ステートメント & #40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-member.md)|計算されるメンバーを作成します。|  
|[CREATE SESSION CUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-session-cube.md)|サーバーのキューブを基にして、同じセッション内のすべてのクエリで使用できるキューブを作成し、データを設定します。|  
|[SET ステートメント & #40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-set.md)|指定されたキューブの名前付きセットを作成します。|  
|[CREATE SUBCUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-subcube.md)|指定されたキューブまたはサブキューブのキューブ空間を指定されたサブキューブに再定義します。|  
|[DROP ACTION ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-action.md)|指定されたキューブから指定されたアクションを削除します。|  
|[DROP CELL CALCULATION ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-cell-calculation.md)|指定されたセル計算を削除します。|  
|[DROP MEMBER ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)|計算されるメンバーを削除します。|  
|[DROP SET ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-set.md)|名前付きセットを削除します。|  
|[DROP SUBCUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-subcube.md)|指定されたサブキューブを削除し、指定された名前の以前のキューブ定義またはサブキューブ定義に戻します。|  
|[更新の CUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-refresh-cube.md)|キューブのクライアント キャッシュを更新します。|  
  
## <a name="see-also"></a>参照  
 [MDX ステートメント リファレンス&#40;MDX&#41;](../mdx/mdx-statement-reference-mdx.md)   
 [MDX データ操作ステートメント&#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [MDX スクリプト ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-scripting-statements-mdx.md)  
  
  
