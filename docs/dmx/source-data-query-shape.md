---
title: 図形 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4d5d93d4236b3cf86719c416ba87517401e4b4f5
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970306"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;ソースデータ &gt; のクエリ-図形
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  複数のデータソースのクエリを1つの階層テーブル (入れ子になったテーブルを含むテーブル) に結合します。これは、マイニングモデルのケーステーブルになります。  
  
 **SHAPE**コマンドの完全な構文については、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Data ACCESS Components (MDAC) ソフトウェア開発キット (SDK) に記載されています。  
  
## <a name="syntax"></a>構文  
  
```  
  
SHAPE {<primary query>}  
APPEND ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>引数  
 *プライマリクエリ*  
 クエリは親テーブルを返します。  
  
 *子テーブルのクエリ*  
 入れ子になったテーブルを返すクエリ。  
  
 *プライマリ列*  
 子テーブルクエリの結果から子行を識別する親テーブル内の列。  
  
 *子列*  
 プライマリクエリの結果から親行を識別する子テーブルの列。  
  
 *列テーブル名*  
 入れ子になったテーブルの親テーブルに、列名を新たに追加します。  
  
## <a name="remarks"></a>注釈  
 親テーブルおよび子テーブルに関連付けられている列によってクエリを並べ替える必要があります。  
  
## <a name="examples"></a>例  
 [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md)ステートメント内で次の例を使用すると、入れ子になったテーブルを含むモデルをトレーニングできます。 **SHAPE**ステートメント内の2つのテーブルは、 **ordernumber**列を介して関連付けられます。  
  
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
 [&#60;ソースデータクエリ&#62;](../dmx/source-data-query.md)   
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
