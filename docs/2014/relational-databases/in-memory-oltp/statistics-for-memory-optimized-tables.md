---
title: メモリ最適化テーブルの統計 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e644766d-1d1c-43d7-83ff-8ccfe4f3af9f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e47a8c6f5b0da31aea9168bbbc56bd9b28afb96
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63155795"
---
# <a name="statistics-for-memory-optimized-tables"></a>メモリ最適化テーブルの統計
  クエリ オプティマイザーでは、クエリのパフォーマンスを向上させるクエリ プランを作成するために列に関する統計を使用します。 統計はデータベースのテーブルから収集され、データベース メタデータに格納されます。  
  
 統計は自動的に作成されますが、手動で作成することもできます。 たとえば、統計は、インデックスの作成時にインデックス キー列に対して自動的に作成されます。 統計の作成の詳細については、「 [Statistics](../statistics/statistics.md)」を参照してください。  
  
 テーブル データは通常、時間の経過に伴い、行が挿入、更新、または削除されて変化します。 これは、統計を定期的に更新する必要があることを意味します。 既定では、ディスク ベース テーブルの統計は、オプティマイザーが統計が古くなったと判断したときに自動的に更新されます。  
  
 メモリ最適化テーブルの統計は、既定では更新されません。 手動で更新する必要があります。 個々の列、インデックス、またはテーブルに対して、 [transact-sql&#41;&#40;UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql)を使用します。 [Sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)を使用して、データベース内のすべてのユーザーと内部テーブルの統計を更新します。  
  
 [CREATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)または[UPDATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/update-statistics-transact-sql)を使用する場合は、メモリ最適化テーブル`NORECOMPUTE`の統計の自動更新を無効にするように指定する必要があります。 ディスクベーステーブルの場合、 [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)は、最後の[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)以降にテーブルが変更されている場合にのみ統計を更新します。 メモリ最適化テーブルの場合、 [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)は常に更新された統計を生成します。 [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)は、メモリ最適化テーブルに適したオプションです。それ以外の場合は、統計を個別に更新できるように、重要な変更が加えられているテーブルを把握しておく必要があります。  
  
 統計は、データのサンプリングまたはフルスキャンの実行によって生成できます。 サンプリング統計は、データ分布を推定するためにテーブル データのサンプルのみを使用します。 フルスキャン統計は、データの分布を調べるためにテーブル全体をスキャンします。 通常、フルスキャン統計の方が正確ですが、計算にかかる時間が長くなります。 サンプリング統計はより速く収集できます。  
  
 ディスク ベース テーブルでは、既定ではサンプリング統計が使用されます。 メモリ最適化テーブルでは、フルスキャン統計のみをサポートしています。 [CREATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)または[UPDATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/update-statistics-transact-sql)を使用する場合は、メモリ最適化テーブルの`FULLSCAN`オプションを指定する必要があります。  
  
 メモリ最適化テーブルの統計に関するその他の注意点を次に示します。  
  
-   メモリ最適化テーブルのインデックスはテーブルを使用して作成されます。 インデックス キー列の統計は、テーブルが空のときに作成されます。 したがって、これらの統計は、データがテーブルに読み込まれた後に更新する必要があります。  
  
-   ネイティブ コンパイル ストアド プロシージャの場合、プロシージャのコンパイル時にプロシージャ内のクエリの実行プランが最適化されます。 これは、統計が更新されたときではなく、プロシージャが作成されたときおよびサーバーが再起動されたときにのみ発生します。 したがって、テーブルには代表的なデータのセットが含まれている必要があり、統計はプロシージャが作成される前に最新の状態にする必要があります  (ネイティブ コンパイル ストアド プロシージャは、データベースがオフラインになってから再度オンラインに戻った場合、またはサーバーが再起動された場合に再コンパイルされます)。  
  
## <a name="guidelines-for-statistics-when-deploying-memory-optimized-tables"></a>メモリ最適化テーブルを配置するときの統計のガイドライン  
 クエリ オプティマイザーでクエリ プランを作成するときに最新の統計が使用されるように、次の 5 つの手順を使用してメモリ最適化テーブルを配置します。  
  
1.  テーブルとインデックスを作成します。 インデックスは、`CREATE TABLE` ステートメントでインラインで指定されます。  
  
2.  テーブルにデータを読み込みます。  
  
3.  テーブル上の統計を更新します。  
  
4.  テーブルにアクセスするストアド プロシージャを作成します。  
  
5.  ワークロードを実行します。これには、ネイティブ コンパイル ストアド プロシージャ、解釈された [!INCLUDE[tsql](../../../includes/tsql-md.md)] ストアド プロシージャ、およびアドホック バッチが混在する場合があります。  
  
 データを読み込んで統計を更新してからネイティブ コンパイル ストアド プロシージャを作成することにより、オプティマイザーで統計をメモリ最適化テーブル用に使用できます。 これによって、プロシージャをコンパイルすると効率的なクエリ プランが作成されます。  
  
## <a name="guidelines-for-maintaining-statistics-on-memory-optimized-tables"></a>メモリ最適化テーブルでの統計の管理のガイドライン  
 統計を最新に保つためには、メモリ最適化テーブルの統計を定期的に更新します。  
  
 データが頻繁に変更される場合は、統計を頻繁に更新する必要があります。 たとえば、バッチ更新の後にテーブルの統計を更新します。 統計を更新した後、更新された統計の利点を得られるように、ネイティブ コンパイル ストアド プロシージャを削除して再作成します。  
  
 .  
  
 ピーク ワークロード中に統計を更新しないでください。  
  
 統計を更新するには:  
  
-   統計[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の[更新タスク](../maintenance-plans/update-statistics-task-maintenance-plan.md)を使用して[メンテナンスプランを作成](../maintenance-plans/create-a-maintenance-plan.md)するには、を使用します  
  
-   または、後で説明する [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを使用して統計を更新します。  
  
 1つのメモリ最適化テーブル (*myschema.xml*) の統計を更新するには *Mytable*)、次のスクリプトを実行します。  
  
```  
UPDATE STATISTICS myschema.Mytable WITH FULLSCAN, NORECOMPUTE  
```  
  
 現在のデータベース内のすべてのメモリ最適化テーブルの統計を更新するには、次のスクリプトを実行します。  
  
```sql  
DECLARE @sql NVARCHAR(MAX) = N''  
  
SELECT @sql += N'  
   UPDATE STATISTICS ' + quotename(schema_name(schema_id)) + N'.' + quotename(name) + N' WITH FULLSCAN, NORECOMPUTE'  
FROM sys.tables WHERE is_memory_optimized=1  
  
EXEC sp_executesql @sql  
```  
  
 データベース内のすべてのテーブルの統計を更新するには、 [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)を実行します。  
  
 次のサンプルでは、メモリ最適化テーブルの最終更新日を報告します。 この情報は、統計を更新する必要があるかどうかを判断するのに役立ちます。  
  
```sql  
select t.object_id, t.name, sp.last_updated as 'stats_last_updated'  
from sys.tables t join sys.stats s on t.object_id=s.object_id cross apply sys.dm_db_stats_properties(t.object_id, s.stats_id) sp  
where t.is_memory_optimized=1  
```  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブル](memory-optimized-tables.md)  
  
  
