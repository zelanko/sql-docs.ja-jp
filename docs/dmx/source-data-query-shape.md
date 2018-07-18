---
title: 図形 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e5c86484252d45c8c7edbd79690159e116d9b3a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985295"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;ソース データ クエリ&gt;-図形
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング モデルのケース テーブルとなる、複数のデータ ソースから単一の階層テーブル (入れ子になったテーブルを使用するテーブル) にクエリを結合します。  
  
 完全な構文、**図形**コマンドが記載されて、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) ソフトウェア開発キット (SDK)。  
  
## <a name="syntax"></a>構文  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>引数  
 *マスターのクエリ*  
 クエリは親テーブルを返します。  
  
 *子テーブルのクエリ*  
 クエリは入れ子になったテーブルを返します。  
  
 *マスターの列*  
 child table query の結果から子の行を識別する親テーブル内の列です。  
  
 *子の列*  
 master query の結果から親の行を識別する子テーブル内の列です。  
  
 *テーブル名の列*  
 入れ子になったテーブルの親テーブルに、列名を新たに追加します。  
  
## <a name="remarks"></a>コメント  
 親テーブルと子テーブルを関連付ける列ごとにクエリを発行する必要があります。  
  
## <a name="examples"></a>使用例  
 内で次の例を使用することができます、 [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md)入れ子になったテーブルを含むモデルをトレーニングするステートメント。 2 つのテーブル内で、**図形**から関連するステートメント、 **OrderNumber**列。  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>参照  
 [&#60;ソース データ クエリ&#62;](../dmx/source-data-query.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
