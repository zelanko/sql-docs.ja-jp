---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47b18dec5466c2eee6e4f945cedb766324e0b4df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177770"
---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41399|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|メッセージ テキスト|並べ替え操作が複雑すぎます。 詳細については、SQL Server オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
 結合操作と集計操作の結果を並べ替えると、並べ替えバッファー内の行のサイズが大きくなり、並べ替え操作の複雑さが増します。 このエラーは、行のサイズが、ネイティブ コンパイル ストアド プロシージャの Sort 演算子でサポートされる最大サイズを超えていることを意味します。 並べ替えバッファー内の行のサイズは、単純に、結合の数および集計関数の数と種類で決まることに注意してください。 ベース テーブル内の行のサイズは、バッファー内の行のサイズに影響しません。  
  
## <a name="user-action"></a>ユーザーの操作  
 結合または集計関数を削除することでクエリの複雑さを軽減してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  