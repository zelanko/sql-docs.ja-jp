---
title: メモリ最適化ハッシュ インデックスで一般的なパフォーマンスの問題のトラブルシューティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1954a997-7585-4713-81fd-76d429b8d095
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 625bde655c6d95ac30966dd39a52534fc5a84299
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083950"
---
# <a name="troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes"></a>メモリ最適化されたハッシュ インデックスのパフォーマンスに関する一般的な問題のトラブルシューティング
  このトピックはハッシュ インデックスの一般的な問題のトラブルシューティングと回避方法に焦点を当てて説明します。  
  
## <a name="search-requires-a-subset-of-hash-index-key-columns"></a>検索を使用するにはハッシュ インデックス キー列のサブセットが必要になる  
 **問題点:** ハッシュ インデックスには、すべての値が、ハッシュ値を計算するためにインデックス キー列と、ハッシュ テーブル内の対応する行を検索が必要とします。 したがって、クエリに WHERE 句のインデックス キーのサブセットのみの等値述語が含まれていると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は WHERE 句の述語に対応する行を検索するインデックス シークを使用できません。  
  
 これに対し、ディスク ベースの非クラスター化インデックスおよびメモリ最適化非クラスター化インデックスのような並べ替えられたインデックスは、インデックス内の先頭列である限り、インデックス キー列のサブセットに対するインデックス シークをサポートします。  
  
 **現象:** この結果、パフォーマンスの低下として[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]をすばやく処理は通常、インデックス シークではなく、フル テーブル スキャンを実行する必要があります。  
  
 **トラブルシューティングを行う方法:** パフォーマンスの低下だけでなく、クエリ プランの検査が、インデックス シークではなくスキャンを示します。 クエリが非常に単純である場合は、クエリ テキストおよびインデックス定義の検査も検索にインデックス キー列のサブセットが必要かどうかを示します。  
  
 次のテーブルとクエリを考えてみます。  
  
```tsql  
CREATE TABLE [dbo].[od]  
(  
     o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
     CONSTRAINT PK_od PRIMARY KEY NONCLUSTERED HASH (o_id, od_id) WITH (BUCKET_COUNT = 10000)  
)  
WITH (MEMORY_OPTIMIZED = ON)  
  
 SELECT p_id  
 FROM dbo.od  
 WHERE o_id=1  
```  
  
 クエリには (o_id) に等値述語がありますが、テーブルには 2 列 (o_id、od_id) にハッシュ インデックスがあります。 クエリにはインデックス キー列のサブセットのみに等値述語があるため、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は PK_od を使用してインデックス シーク操作を実行できません。代わりに、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はフル インデックス スキャンに戻す必要があります。  
  
 **回避策:** はさまざまな回避策があります。 以下に例を示します。  
  
-   インデックスを非クラスター化ハッシュではなく非クラスター化型として再作成します。 メモリ最適化非クラスター化インデックスが順序付きであるため、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は先頭のインデックス キー列のインデックス シークを実行できます。 例の結果の主キーの定義は `constraint PK_od primary key nonclustered` です。  
  
-   WHERE 句の列と一致するように現在のインデックス キーを変更します。  
  
-   クエリの WHERE 句の列と一致する新しいハッシュ インデックスを追加します。 例では、結果のテーブル定義は次のようになります:  
  
    ```tsql  
    CREATE TABLE dbo.od  
     ( o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
  
     CONSTRAINT PK_od PRIMARY KEY   
     NONCLUSTERED HASH (o_id,od_id) WITH (BUCKET_COUNT=10000),  
  
     INDEX ix_o_id NONCLUSTERED HASH (o_id) WITH (BUCKET_COUNT=10000)  
  
     ) WITH (MEMORY_OPTIMIZED=ON)  
    ```  
  
 特定のインデックス キー値に多くの重複する行がある場合、メモリ最適化ハッシュ インデックスは適切に機能しないことに注意してください: 例では、列 o_id の一意の値の数がテーブルの行数よりもかなり少ない場合、(o_id) のインデックスを追加することは最適ではなく、代わりに、インデックス PK_od の種類をハッシュから非クラスター化に変更することがより適切な解決策です。 詳細については、次を参照してください。[ハッシュ インデックスの適切なバケット数を決定する](../relational-databases/indexes/indexes.md)です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルのインデックス](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  