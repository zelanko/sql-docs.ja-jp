---
title: "解釈された Transact-SQL を使用したメモリ最適化テーブルへのアクセス | Microsoft Docs"
ms.custom: 
ms.date: 05/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 67e5fad803b006dfe1aaf8794c440747db285c4f
ms.lasthandoff: 04/11/2017

---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a>解釈された Transact-SQL を使用したメモリ最適化テーブルへのアクセス
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

 いくつかの例外を除き、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリまたは DML 操作 (選択、挿入、更新、または削除)、アドホック バッチ、および SQL モジュール (ストアド プロシージャ、テーブル値関数、トリガー、ビューなど) を使用して、メモリ最適化テーブルにアクセスできます。  
  
インタープリターによって処理される [!INCLUDE[tsql](../../includes/tsql-md.md)] とは、ネイティブ コンパイル ストアド プロシージャとは異なる、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチまたはストアド プロシージャを意味します。 インタープリターによって処理される [!INCLUDE[tsql](../../includes/tsql-md.md)] による、メモリ最適化されたテーブルへのアクセスは、相互運用アクセスと呼ばれます。  

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降では、解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] のクエリは、直列モードだけではなく、並列でもメモリ最適化テーブルをスキャンできます。

メモリ最適化テーブルには、ネイティブ コンパイル ストアド プロシージャを使用してアクセスすることもできます。 ネイティブ コンパイル ストアド プロシージャは、パフォーマンスが重要な OLTP 操作に推奨されます。  
  
解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] によるアクセスは、次のシナリオにお勧めします。  
  
- アドホック クエリおよび管理タスク。  
  
- レポート クエリ。このクエリでは通常、ネイティブ コンパイル ストアド プロシージャでは使用できない構造 ( *ウィンドウ* 関数など) を使用します (ウィンドウ関数は [OVER](../../t-sql/queries/select-over-clause-transact-sql.md) 関数とも呼ばれます)。  
  
- アプリケーション コードの変更を最小限に抑えて (またはコードを変更することなく)、アプリケーションのパフォーマンスが重要な部分をメモリ最適化テーブルに移行するには、次の手順を実行します。 テーブルを移行すると、パフォーマンス向上を確認できることがあります。 ストアド プロシージャをネイティブ コンパイル ストアド プロシージャに移行すると、いっそうのパフォーマンス向上が確認されることがあります。  
  
- ネイティブ コンパイル ストアド プロシージャでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用できません。  
  
ただし、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] 構造は、メモリ最適化されたテーブル内のデータにアクセスする、インタープリターによって処理される [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャでサポートされていません。  
  
|領域|サポートされていない|  
|----------|-----------------|  
|テーブルへのアクセス|TRUNCATE TABLE<br /><br /> MERGE (ターゲットとしてのメモリ最適化テーブル)<br /><br /> 動的カーソルおよびキーセット カーソル (これらは自動的に静的カーソルに降格されます)。<br /><br /> コンテキスト接続を使用した CLR モジュールからのアクセス。<br /><br /> インデックス付きビューから、メモリ最適化されたテーブルへの参照。|  
|複数のデータベース間|複数データベースにまたがるクエリ<br /><br /> 複数データベースにまたがるトランザクション<br /><br /> リンク サーバー|  
  
## <a name="table-hints"></a>テーブル ヒント

テーブル ヒントの詳細については、 [テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md). [!INCLUDE[hek_2](../../includes/hek-2-md.md)] をサポートするために SNAPSHOT が追加されました。  
  
次のテーブル ヒントは、解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してメモリ最適化テーブルにアクセスする場合はサポートされません。  

  
|||||  
|-|-|-|-|  
|HOLDLOCK|IGNORE_CONSTRAINTS|IGNORE_TRIGGERS|NOWAIT|  
|PAGLOCK|READCOMMITTED|READCOMMITTEDLOCK|READPAST|  
|READUNCOMMITTED|ROWLOCK|SPATIAL_WINDOW_MAX_CELLS = *integer*|TABLOCK|  
|TABLOCKXX|UPDLOCK|XLOCK||  
  

解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して明示的または暗黙のトランザクションからメモリ最適化テーブルにアクセスする場合には、次の操作のうち少なくとも 1 つを実行する必要があります:  
  
- SNAPSHOT、REPEATABLEREAD、SERIALIZABLE などの [分離レベルのテーブル ヒント](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md) を指定する。  
  
- データベース オプション [MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT](../../t-sql/statements/alter-database-transact-sql-set-options.md) を ON に設定する。  
  
[自動コミット モード](http://msdn.microsoft.com/en-us/c8de5b60-d147-492d-b601-2eeae8511d00)で実行されるクエリでアクセスするメモリ最適化テーブルの場合、分離レベルのテーブル ヒントは必要ありません。  
  
## <a name="see-also"></a>参照

[Transact-SQL によるインメモリ OLTP のサポート](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   

[インメモリ OLTP への移行](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  


