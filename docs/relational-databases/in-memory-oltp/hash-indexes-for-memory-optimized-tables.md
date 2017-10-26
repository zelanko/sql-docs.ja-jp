---
title: "メモリ最適化テーブルのハッシュ インデックス | Microsoft Docs"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.service: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e922cc3a-3d6e-453b-8d32-f4b176e98488
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b1acbcd97dfabfa5d23fa82e55d4eb01101233aa
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="hash-indexes-for-memory-optimized-tables"></a>メモリ最適化テーブルのハッシュ インデックス
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
ここでは、メモリ最適化テーブルで利用可能な*ハッシュ*型インデックスについて説明します。 記事の内容は次のとおりです。  
  
- Transact-SQL 構文を説明する短いコード例を示します。  
- ハッシュ インデックスの基礎について説明します。  
- [適切なバケット数を見積もる方法](#configuring_bucket_count)について説明します。  
- ハッシュ インデックスの設計と管理方法について説明します。  
  
  
#### <a name="prerequisite"></a>前提条件  
  
この記事を理解するための重要なコンテキスト情報は、次の記事に収められています。  
  
- [メモリ最適化テーブルのインデックス](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)  
  
  
  
## <a name="a-syntax-for-memory-optimized-indexes"></a>A. メモリ最適化インデックスの構文  
  
  
### <a name="a1-code-sample-for-syntax"></a>A.1 構文のコード例  
  
ここには、メモリ最適化テーブルのハッシュ インデックスを作成する際に使用できる構文を示す Transact-SQL コード ブロックが含まれています。  
  
- このサンプルは、CREATE TABLE ステートメント内でハッシュ インデックスが宣言されることを示しています。  
  - 代わりに、別個の [ALTER TABLE...ADD INDEX](#h3-b2-declaration-limitations) ステートメントでハッシュ インデックスを宣言することもできます。  
  
  
  
    DROP TABLE IF EXISTS SupportEventHash;  
    go  
      
    CREATE TABLE SupportIncidentRating_Hash  
    (  
      SupportIncidentRatingId   int      not null   identity(1,1)  
        PRIMARY KEY NONCLUSTERED,  
      
      RatingLevel          int           not null,  
      
      SupportEngineerName  nvarchar(16)  not null,  
      Description          nvarchar(64)      null,  
      
      INDEX ix_hash_SupportEngineerName  
        HASH (SupportEngineerName) WITH (BUCKET_COUNT = 100000)  
    )  
      WITH (  
        MEMORY_OPTIMIZED = ON,  
        DURABILITY = SCHEMA_ONLY);  
    go  
  

データの適切な `BUCKET_COUNT` を決定するには、「 [ハッシュ インデックスのバケット数の構成](#configuring_bucket_count)」を参照してください。 
  
## <a name="b-hash-indexes"></a>B. ハッシュ インデックス  
  
  
### <a name="b1-performance-basics"></a>B.1 パフォーマンスの基礎  
  
ハッシュ インデックスのパフォーマンスは次のようになります。  
  
- WHERE 句がハッシュ インデックス キーの各列の *正確な* 値を指定する場合は、極めて良好です。  
- WHERE 句がインデックス キーで値の *範囲* を探す場合は、よくありません。  
- WHERE 句が 2 列のハッシュ インデックス キーの最初の列の特定の値を指定するが、キーの *2* 番目の列の値を指定しない場合は、よくありません。  
  
  
<a name="h3-b2-declaration-limitations"></a>  
  
### <a name="b2-declaration-limitations"></a>B.2 宣言の制限  
  
ハッシュ インデックスは、メモリ最適化テーブルにのみ存在できます。 ディスク ベース テーブルには存在できません。  
  
ハッシュ インデックスは、次のように宣言できます。  
  
- UNIQUE。そうしないと、既定の Nonunique になります。  
- NONCLUSTERED (既定値)。   
  
  
CREATE TABLE ステートメント外でハッシュ インデックスを作成する構文の例を次に示します。  
  
  
    ALTER TABLE MyTable_memop  
      ADD INDEX ix_hash_Column2 UNIQUE  
        HASH (Column2) WITH (BUCKET_COUNT = 64);  
  
  
  
### <a name="b3-buckets-and-hash-function"></a>B.3 バケットとハッシュ関数  
  
ハッシュ インデックスでは、 *バケット* 配列と呼ばれるものの中に、そのキー値を固定します。  
  
- 各バケットは 8 バイトであり、キー エントリのリンク リストのメモリ アドレスを格納するために使用されます。  
- 各エントリは、インデックス キーの値と、基になるメモリ最適化テーブル内の対応する行のアドレスです。  
  - 各エントリは、すべて現在のバケットにチェーンされたエントリのリンク リスト内の次のエントリを指します。  
  
  
ハッシュ アルゴリズムはすべての一意キー値または個別キー値をそのバケット間に均等に分散しようとしますが、完全に均等になることは現実にはありえません。 ある特定のキー値のすべてのインスタンスは、同じバケットにチェーンされます。 そのバケットに別のキー値のすべてのインスタンスが混在する場合もあります。  
  
- この混在は *ハッシュの競合*と呼ばれます。 競合は一般的ですが、理想的ではありません。  
- 現実的な目標は、バケットの 30% に 2 つの異なるキー値が含まれていることです。  
  
  
ハッシュ インデックスが持つべきバケットの数を宣言する必要があります。  
  
- テーブルの行数または個別の値の数に対するバケット数の割合が低ければ低いほど、バケットの平均リンク リストは長くなります。  
- 短いリンク リストは、長いリンク リストよりも高速で実行されます。  
  
  
SQL Server には、すべてのハッシュ インデックスで使用するハッシュ関数が 1 つあります。  
  
- このハッシュ関数は決定論的であり、同じ入力キー値を与えると、一貫して同じバケット スロットを出力します。  
- 呼び出しを繰り返すと、ハッシュ関数の出力は、フラットな線形分布ではなく、ポワソン分布または釣鐘曲線分布を形成する傾向があります。  
  
  
ハッシュ インデックスとバケットの関係をまとめると、次の図のようになります。  
  
  
![hekaton_tables_23d](../../relational-databases/in-memory-oltp/media/hekaton-tables-23d.png "インデックス キーがハッシュ関数に入力され、ハッシュ バケットのアドレスが出力されます。これはチェーンの先頭を示します。")  
  
  
  
### <a name="b4-row-versions-and-garbage-collection"></a>B.4 行のバージョンとガベージ コレクション  
  
  
メモリ最適化テーブルでは、行が SQL UPDATE による影響を受ける場合、テーブルで行の更新バージョンが作成されます。 更新トランザクションの間、他のセッションは行の前のバージョンを読み取ることができるため、行ロックに関連するパフォーマンスの低下を回避することができます。  
  
ハッシュ インデックスに、更新に対応するための異なるバージョンのエントリも存在することがあります。  
  
後で前のバージョンが不要になったときに、ガベージ コレクション (GC) スレッドがバケットとそのリンク リストを横断して、前のエントリをクリーンアップします。 GC スレッドのパフォーマンスは、リンク リストのチェーン長が短い場合に優れています。   
  
<a name="configuring_bucket_count"></a>
  
## <a name="c-configuring-the-hash-index-bucket-count"></a>C. ハッシュ インデックスのバケット数の構成  
  
ハッシュ インデックスのバケット数はインデックス作成時に指定しますが、ALTER TABLE...ALTER INDEX REBUILD 構文を使用して変更することができます。  
  
ほとんどの場合、バケット数は、理想的にはインデックス キーの個別の値の数の 1 から 2 倍の範囲内にします。   
特定のインデックス キーに値がどれぐらいあるかは、予測できないこともあります。 **BUCKET_COUNT** 値がキー値の実際の数の 10 倍以内であれば、パフォーマンスは通常まだ良好であり、低く見積もるよりは多く見積もりすぎるほうが一般的によい結果が得られます。  
  
*少なすぎる* バケットには、次の短所があります。  
  
- 個別のキー値のハッシュの競合の増加。  
  - 個別の値が、異なる個別の値を持つバケットの共有を強いられます。  
  - パケットごとの平均チェーン長が増えます。  
  - バケット チェーンが長ければ長いほど、インデックスでの等値検索の速度が遅くなります。  
  
*多すぎる* バケットには、次の短所があります。  
  
- バケット数が高すぎると、空のバケットを増やす結果になることがあります。  
  - 空のバケットは、フル インデックス スキャンのパフォーマンスに影響を与えます。 フル インデックス スキャンが普通に行われる場合は、インデックス キーの個別の値の数に近いバケット数を選択することを検討してください。  
  - 空のバケットは、それぞれが使用するのはわずか 8 バイトですが、メモリを使用します。  
    
  
> [!NOTE]
> バケットを追加しても、重複する値を共有するエントリのチェーンが短くなることはありません。 値の重複の割合は、ハッシュが適切なインデックスの種類であるかどうかを決定するために使用され、バケット数を計算するために使用されることはありません。  
  
  
  
### <a name="c1-practical-numbers"></a>C.1 実際的な数値  
  
**BUCKET_COUNT** が推奨される範囲を多少逸脱している場合でも、ハッシュ インデックスのパフォーマンスは、許容できるか容認できる可能性があります。 危機は発生しません。  
  
ハッシュ インデックスの **BUCKET_COUNT** には、メモリ最適化テーブルが増大すると予測される行数とほぼ等しい値を指定します。  
  
テーブルに 2,000,000 の行があるが、その数が 10 倍の 20,000, 000 行に増大すると予測していると仮定します。 テーブル内の行数の 10 倍のバケット数から始めます。 これにより、行数の増加に対応する余地ができます。  
  
- 理想的には、行数が最初のバケット数に達したときに、バケット数を増やすことになります。  
- 行数がバケット数の 5 倍に増大したとしても、多くの場合、パフォーマンスは良好です。  
  
ハッシュ インデックスに 10,000, 000 の個別のキー値があると仮定します。  
  
- バケット数 2,000,000 は、容認できるほぼ最低の値です。 パフォーマンスの低下の度合いは、許容できる可能性があります。  
  
### <a name="c2-too-many-duplicate-values-in-the-index"></a>C.2 インデックス内の重複する値が多すぎる  
  
ハッシュ インデックス値の重複率が高いと、ハッシュ バケットのチェーンが長くなります。  
  
前の T-SQL 構文のコード ブロックと同じ SupportEvent テーブルがあると仮定します。 次の T-SQL コードは、 *すべての* 値の *一意の* 値に対する比率を検出して表示する方法を示しています。  
  
        -- Calculate ratio of:  Rows / Unique_Values.  
    DECLARE @allValues float(8) = 0.0, @uniqueVals float(8) = 0.0;  
      
    SELECT @allValues = Count(*) FROM SupportEvent;  
      
    SELECT @uniqueVals = Count(*) FROM  
      (SELECT DISTINCT SupportEngineerName  
         FROM SupportEvent) as d;  
      
        -- If (All / Unique) >= 10.0, use a nonclustered index, not a hash.   
    SELECT Cast((@allValues / @uniqueVals) as float) as [All_divby_Unique];  
    go  
  
- 比率 10.0 以上は、インデックスの種類としてハッシュは適していないことを意味します。 代わりに非クラスター化インデックスを使用することを検討してください。   
  
## <a name="d-troubleshooting-hash-index-bucket-count"></a>D. ハッシュ インデックスのバケット数のトラブルシューティング  
  
このセクションでは、ハッシュ インデックスのバケット数のトラブルシューティング方法について説明します。  
  
### <a name="d1-monitor-statistics-for-chains-and-empty-buckets"></a>D.1 チェーンと空のバケットの統計を監視する  
  
次の T-SQL SELECT を実行することで、ハッシュ インデックスの統計を監視できます。 この SELECT では、 **sys.dm_db_xtp_hash_index_stats**という名前のデータ管理ビュー (DMV) を使用します。  
  
  
```t-sql
  SELECT  
    QUOTENAME(SCHEMA_NAME(t.schema_id)) + N'.' + QUOTENAME(OBJECT_NAME(h.object_id)) as [table],   
    i.name                   as [index],   
    h.total_bucket_count,  
    h.empty_bucket_count,  
      
    FLOOR((  
      CAST(h.empty_bucket_count as float) /  
        h.total_bucket_count) * 100)  
                             as [empty_bucket_percent],  
    h.avg_chain_length,   
    h.max_chain_length  
  FROM  
         sys.dm_db_xtp_hash_index_stats  as h   
    JOIN sys.indexes                     as i  
            ON h.object_id = i.object_id  
           AND h.index_id  = i.index_id  
    JOIN sys.memory_optimized_tables_internal_attributes ia ON h.xtp_object_id=ia.xtp_object_id
    JOIN sys.tables t on h.object_id=t.object_id
  WHERE ia.type=1
  ORDER BY [table], [index];  
```
  
  
SELECT の結果を、次の統計ガイドラインと比較します。  
  
- 空のバケット:  
  - 33% は適切な目標値ですが、通常は、より大きなパーセント値 (ちょうど 90%) がふさわしい値となります。  
  - バケット数が個別のキー値の数と等しい場合は、バケットの約 33% が空です。  
  - 10% 未満の値は低すぎます。  
- バケット内のチェーン:  
  - 平均チェーン長は、重複するインデックス キーの値がない場合、1 が最適です。 通常、10 までのチェーン長を使用できます。  
  - 平均チェーン長が 10 より大きく、空のバケットの割合が 10% を超える場合、非常に多くのデータが重複しているため、ハッシュ インデックスは最も適切な種類ではない可能性があります。  
  

  
### <a name="d2-demonstration-of-chains-and-empty-buckets"></a>D.2 チェーンと空のバケットのデモンストレーション  
  
  
次の T-SQL コード ブロックを使用すると、 `SELECT * FROM sys.dm_db_xtp_hash_index_stats;`を簡単にテストできます。 このコード ブロックは 1 分で完了します。 次のコード ブロックのフェーズを以下に示します。  
  
  
1. いくつかのハッシュ インデックスがあるメモリ最適化テーブルを作成します。  
2. テーブルに数千行を設定します。  
    A. モジュロ演算子を使用して、StatusCode 列の重複する値の割合を構成します。  
    B. INSERT ループは、262144 行を約 1 分間で挿入します。  
3. PRINT は、前述の SELECT を **sys.dm_db_xtp_hash_index_stats**から実行することを指示するメッセージを出力します。  
  
  
```t-sql
    DROP TABLE IF EXISTS SalesOrder_Mem;  
    go  
      
      
    CREATE TABLE SalesOrder_Mem  
    (  
      SalesOrderId   uniqueidentifier  NOT NULL  DEFAULT newid(),  
      OrderSequence  int               NOT NULL,  
      OrderDate      datetime2(3)      NOT NULL,  
      StatusCode     tinyint           NOT NULL,  
      
      PRIMARY KEY NONCLUSTERED  
          HASH (SalesOrderId)  WITH (BUCKET_COUNT = 262144),  
      
      INDEX ix_OrderSequence  
          HASH (OrderSequence) WITH (BUCKET_COUNT = 20000),  
      
      INDEX ix_StatusCode  
          HASH (StatusCode)    WITH (BUCKET_COUNT = 8),  
      
      INDEX ix_OrderDate       NONCLUSTERED (OrderDate DESC)  
    )  
      WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
    go  
      
        --------------------  
      
    SET NoCount ON;  
      
      -- Same as PK bucket_count.  68 seconds to complete.  
    DECLARE @i int = 262144;  
      
    BEGIN TRANSACTION;  
      
    WHILE @i > 0  
    Begin  
      
      INSERT SalesOrder_Mem  
          (OrderSequence, OrderDate, StatusCode)  
        Values  
          (@i, GetUtcDate(), @i % 8);  -- Modulo technique.  
      
      SET @i -= 1;  
    End  
    COMMIT TRANSACTION;  
      
    PRINT 'Next, you should query:  sys.dm_db_xtp_hash_index_stats .';  
    go  
```  
  
  
前述の INSERT ループは、次の操作を行います。  
  
- 主キー インデックスと ix_OrderSequence に一意の値を挿入します。  
- StatusCode の 8 つのみの個別の値を表す 20 ～ 30 万の行を挿入します。 したがって、ix_StatusCode インデックスの値は高い割合で重複しています。  
  
バケット数が最適でない場合のトラブルシューティングを行うために、 **sys.dm_db_xtp_hash_index_stats**からの SELECT の次の出力を確認します。 これらの結果を得るために、セクション D.1 からコピーした SELECT に `WHERE Object_Name(h.object_id) = 'SalesOrder_Mem'` を追加しています。  
  
  
  
SELECT の結果をコードの後に示しています。見やすくするために、結果を幅の狭い 2 つの結果表に意図的に分割しています。  
  
- *バケット数*に関する結果は次のとおりです。  
  
  
| IndexName | total_bucket_count | empty_bucket_count | EmptyBucketPercent |  
| :-------- | -----------------: | -----------------: | -----------------: |  
| ix_OrderSequence | 32768 | 13 | 0 |  
| ix_StatusCode | 8 | 4 | 50 |  
| PK_SalesOrd_B14003... | 262144 | 96525 | 36 |  
  
  
- *チェーン長*に関する結果を次に示します。  
  
  
| IndexName | avg_chain_length | max_chain_length |  
| :-------- | ---------------: | ---------------: |  
| ix_OrderSequence | 8 | 26 |  
| ix_StatusCode | 65536 | 65536 |  
| PK_SalesOrd_B14003... | 1 | 8 |  
  
  
  
  
これらの結果表から、3 つのハッシュ インデックスを解釈してみましょう。  
  
*ix_StatusCode:*  
  
- バケットの 50% が空です。これは適切な値です。  
- ただし、平均チェーン長が非常に高くなっています (65,536)。  
  - これは、重複する値の割合が高いことを示しています。  
  - したがって、この場合は、ハッシュ インデックスの使用は適切ではありません。 代わりに、非クラスター化インデックスを使用する必要があります。  
  
*ix_OrderSequence:*  
  
- バケットの 0% が空です。この値は低すぎます。  
- このインデックスのすべての値が一意であっても、平均チェーン長は 8 になっています。  
  - したがって、バケット数を増やして、平均チェーン長が 2 または 3 に近づくまで減らす必要があります。  
- インデックス キーには 262,144 個の一意の値があるため、バケット数は最低でも 262,144 にする必要があります。  
  - 今後の増大が予測される場合、バケット数はさらに高くする必要があります。  
  
*Primary key index (PK_SalesOrd_...):*  
  
- バケットの 36% が空です。これは適切な値です。  
- 平均チェーン長は 1 であり、これも適切な値です。 変更は不要です。  
  
  
### <a name="d3-balancing-the-trade-off"></a>D.3 トレードオフのバランスを考慮する  
  
OLTP ワークロードは、個々の行に注目します。 フル テーブル スキャンは、通常は OLTP ワークロードのパフォーマンスのクリティカル パスではありません。 したがって、トレードオフのバランスを考慮する必要があるのは、次の項目の間です。  
  
- メモリの使用量  
- 等値テストと挿入操作のパフォーマンス  
  
  
*メモリの使用量のほうが大きな問題である場合:*  
  
- インデックス キー レコードの数に近いバケット数を選択します。  
- バケット数は、インデックス キー値の数より大幅に小さくならないようにする必要があります。大幅に小さい場合、ほとんどの DML 操作や、サーバーの再起動後のデータベースの復旧に要する時間にも影響があります。  
  
  
*等値テストのパフォーマンスのほうが大きな問題である場合:*  
  
- 一意のインデックス値の数の 2 倍または 3 倍のバケット数が適しています。 高いバケット数は、次のことを意味します。  
  - 1 つの特定の値を検索する場合の高速での取得。  
  - メモリ使用率の上昇。  
  - ハッシュ インデックスのフル スキャンに必要な時間の増加。  
  
  
  
  
## <a name="e-strengths-of-hash-indexes"></a>E. ハッシュ インデックスの強み  
  
  
ハッシュ インデックスは、次に該当する場合に非クラスター化インデックスよりも適しています。  
  
- クエリで、次に示すように、等値を指定する WHERE 句を使用してインデックス付き列をテストする。  
  
  
  
    SELECT col9 FROM TableZ  
        WHERE Z_Id = 2174;  
  
  
  
### <a name="e1-multi-column-hash-index-keys"></a>E.1 複数列のハッシュ インデックス キー  
  
  
2 列のインデックスは、非クラスター化インデックスにすることも、ハッシュ インデックスにすることもできます。 インデックスの列が col1 と col2 であるとします。 次の SQL SELECT ステートメントの場合、クエリ オプティマイザーにとって役立つのは、非クラスター化インデックスのみになります。  
  
  
    SELECT col1, col3  
        FROM MyTable_memop  
        WHERE col1 = 'dn';  
  
  
ハッシュ インデックスを使用するには、キーの列それぞれについて、WHERE 句が等値テストを指定する必要があります。 そうしないと、オプティマイザーにとってハッシュ インデックスは役に立ちません。  
  
インデックス キーの 2 番目の列のみ WHERE 句が指定した場合は、どちらの種類のインデックスも役に立ちません。  

