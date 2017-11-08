---
title: "DBCC CHECKTABLE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKTABLE_TSQL
- DBCC_CHECKTABLE_TSQL
- DBCC CHECKTABLE
- CHECKTABLE
dev_langs:
- TSQL
helpviewer_keywords:
- indexed views [SQL Server], DBCC CHECKTABLE
- page integrity checks [SQL Server]
- consistency [SQL Server], tables
- consistency [SQL Server], indexed views
- DBCC CHECKTABLE statement
- integrity [SQL Server]
- low overhead checks
- table integrity checks [SQL Server]
ms.assetid: 0d6cb620-eb58-4745-8587-4133a1b16994
caps.latest.revision: 89
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: af19e042e9e40bd92352a175394c442431959b0e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-checktable-transact-sql"></a>DBCC CHECKTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] すべてのページと、テーブルまたはインデックス付きビューを構成する構造の整合性を確認します。
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
    
## <a name="syntax"></a>構文    
    
```sql
    
DBCC CHECKTABLE     
(    
    table_name | view_name    
    [ , { NOINDEX | index_id }    
     |, { REPAIR_ALLOW_DATA_LOSS | REPAIR_FAST | REPAIR_REBUILD }     
    ]     
)    
    [ WITH     
        { ALL_ERRORMSGS ]    
          [ , EXTENDED_LOGICAL_CHECKS ]     
          [ , NO_INFOMSGS ]    
          [ , TABLOCK ]     
          [ , ESTIMATEONLY ]     
          [ , { PHYSICAL_ONLY | DATA_PURITY } ]     
          [ , MAXDOP = number_of_processors ]    
        }    
    ]    
```    
    
## <a name="arguments"></a>引数    
 *table_name* | *view_name*  
 整合性チェックを行うテーブルまたはインデックス付きビューを指定します。 テーブルまたはビューの名前は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
    
 NOINDEX  
 ユーザー テーブルの非クラスター化インデックスの集中チェックを実行しないように指定します。 これにより、全体の実行時間が短縮されます。 整合性チェックは、常にすべてのシステム テーブルのインデックスに対して実行されるため、NOINDEX はシステム テーブルに対しては無効です。  
    
 *index_id*  
 整合性チェックを行うインデックスの識別 (ID) 番号を指定します。 場合*index_id*を指定すると、DBCC CHECKTABLE は、そのインデックス、ヒープまたはクラスター化インデックスに対してのみ整合性チェックを実行します。  
    
 REPAIR_ALLOW_DATA_LOSS | REPAIR_FAST | REPAIR_REBUILD  
 検出されたエラーを DBCC CHECKTABLE が修復するように指定します。 修復オプションを使用するには、データベースがシングル ユーザー モードになっている必要があります。  
    
 REPAIR_ALLOW_DATA_LOSS  
 報告されたすべてのエラーの修復を試みます。 修復を実行すると、データが失われることがあります。  
    
 REPAIR_FAST  
 構文は、旧バージョンとの互換性のためにのみ残されています。 修復操作は実行されません。  
    
 REPAIR_REBUILD  
 データ損失の可能性がない修復を実行します。 これには、非クラスター化インデックスの存在しない行の修復など時間のかからない修復操作と、インデックスの再構築など時間のかかる修復操作が含まれます。  
 この引数では、FILESTREAM データに関係するエラーは修復されません。  
    
 > [!NOTE]  
 >  REPAIR オプションは、最後の手段としてのみ使用してください。 エラーの修復では、バックアップから復元することをお勧めします。 修復操作では、テーブルまたはテーブル間に制約があっても考慮されません。 指定したテーブルに 1 つでも関連する制約がある場合は、修復操作の後に DBCC CHECKCONSTRAINTS を実行することをお勧めします。 REPAIR を使用する必要がある場合は、修復オプションを指定せずに DBCC CHECKTABLE を実行して、使用する修復レベルを確認してください。 REPAIR_ALLOW_DATA_LOSS レベルを使用する場合は、このオプションを指定して DBCC CHECKTABLE を実行する前に、データベースをバックアップすることをお勧めします。  
    
 ALL_ERRORMSGS  
 エラーを無制限に表示します。 既定では、すべてのエラー メッセージが表示されます。 そのため、このオプションを指定しても省略しても影響はありません。  
    
 EXTENDED_LOGICAL_CHECKS  
 互換性レベルが 100 の場合 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) または存在する場合、以降では、インデックス付きビュー、XML インデックス、および空間インデックスは、論理的な一貫性チェックを実行します。  
 詳細については、このトピックの「解説」の「インデックスに対する論理的な一貫性チェックの実行」を参照してください。  
    
 NO_INFOMSGS  
 すべての情報メッセージを表示しないようにします。  
    
 TABLOCK  
 DBCC CHECKTABLE が、内部データベースのスナップショットを使用するのではなく、共有テーブル ロックを取得します。 TABLOCK の作用によって負荷の高いテーブルでも DBCC CHECKTABLE の実行速度が速くなりますが、DBCC CHECKTABLE の実行中はテーブルでの同時実行性が低下します。  
    
 ESTIMATEONLY  
 その他のすべての指定したオプションで DBCC CHECKTABLE を実行するために必要な tempdb 領域の推定サイズが表示されます。  
    
 PHYSICAL_ONLY  
 チェック内容を、ページ、レコード ヘッダー、および B-Tree の物理構造の整合性に限定します。 テーブルの物理的一貫性に関する低オーバーヘッド チェックを提供するように設計されているため、このチェックではデータが損傷する可能性のある破損ページおよび一般的なハードウェア障害も検出できます。 完全な DBCC CHECKTABLE を実行すると、以前のバージョンよりはるかに時間がかかることがあります。 原因は次のとおりです。  
 -   論理チェックの対象範囲が広がった。  
 -   チェック対象の、基になる構造の一部が複雑になった。  
 -   新機能を含めるために多数の新しいチェックが導入された。  
   
 したがって、大規模なテーブルでは、PHYSICAL_ONLY オプションを使用すると DBCC CHECKTABLE の実行時間が大幅に短縮されることがあるため、実稼働システムで頻繁に使用する場合はこのオプションを使用することをお勧めします。 ただし、完全な DBCC CHECKTABLE を定期的に実行することもお勧めします。 実行する頻度は、それぞれの業務環境や運用環境に固有の要因によって異なります。 PHYSICAL_ONLY を指定した場合は常に NO_INFOMSGS も暗黙的に指定されるため、修復オプションを同時指定することはできません。  
    
 > [!NOTE]  
 >  PHYSICAL_ONLY を指定すると、DBCC CHECKTABLE で FILESTREAM データのチェックがすべてスキップされるようになります。  
    
 DATA_PURITY  
 DBCC CHECKTABLE によって、テーブル内に無効な列値または範囲外の列値が含まれていないかチェックされます。 たとえば、DBCC CHECKTABLE がより大きいか、許容範囲よりも少ないの日付と時刻の値を持つ列を検出、 **datetime**データ型または**decimal**型または概数データ型無効な小数点以下桁数または有効桁数の値を持つ列。  
 列の値の整合性チェックは既定で有効になっているため、DATA_PURITY オプションを指定する必要はありません。 以前のバージョンからアップグレードしたデータベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、検索、特定のテーブルのエラーを修正して、DBCC CHECKTABLE WITH DATA_PURITY を使用できますただし、テーブルの列の値のチェックを無効になって既定で DBCC CHECKDB WITH DATA_PURITY まで。データベースでエラーがないを実行されています。 DBCC CHECKDB および DBCC CHECKTABLE によって、列値の整合性が既定でチェックされるようになります。  
 DBCC 修復オプションを使用して、このオプションによって報告された検証エラーを修正することはできません。 これらのエラーを手動で修正する方法については、サポート技術情報の資料 923247 を参照してください: [SQL Server 2005 およびそれ以降のバージョンでのトラブルシューティングの DBCC エラー 2570](http://support.microsoft.com/kb/923247)です。  
 PHYSICAL_ONLY を指定した場合は、列の整合性チェックは行われません。  
    
 MAXDOP  
 **適用されます**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を通じて 2014 SP2[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)します。  
 上書き、**並列処理の次数の最大**構成オプションの**sp_configure**ステートメントです。 MAXDOP では、sp_configure で構成されている値を超えることができます。 MAXDOP では、リソース ガバナーで構成されている値を超えると、データベース エンジンは、ALTER WORKLOAD GROUP (TRANSACT-SQL)」に記載のリソース ガバナーの MAXDOP 値を使用します。 MAXDOP クエリ ヒントを使用している場合は、max degree of parallelism 構成オプションで使用されるすべての意味ルールを適用できます。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。  
    
 > [!CAUTION]  
 >  MAXDOP が 0 に設定されている場合、サーバーでは最大限の並列処理が実行されます。  
    
## <a name="remarks"></a>解説    
    
> [!NOTE]    
>  データベース内の各テーブルで DBCC CHECKTABLE を実行する[DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)です。    
    
指定したテーブルについて、次の項目がチェックされます。
-   インデックス、行、LOB、および行オーバーフロー データの各ページが正しくリンクされていること。    
-   インデックスが正しい並べ替え順序で並んでいること。    
-   ポインターに一貫性があること。    
-   各ページ上のデータが、計算列も含め、適切であること。    
-   ページ オフセットが適切であること。    
-   ベース テーブルと各非クラスター化インデックスのすべての行がそれぞれに対応していること。    
-   パーティション テーブルやパーティション インデックスのすべての行が正しいパーティションにあること。    
-   格納するときに、ファイル システムとテーブル間の一貫性をリンク-レベル**varbinary (max)** FILESTREAM を使用して、ファイル システム内のデータ。    
    
## <a name="performing-logical-consistency-checks-on-indexes"></a>インデックスに対する論理的な一貫性チェックの実行    
インデックスに対する論理的な一貫性チェックは、データベースの互換性レベルによって次のように異なります。
-   互換性レベルが 100 の場合 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) またはそれ以降。    
    -   NOINDEX が指定されていない場合、DBCC CHECKTABLE は、1 つのテーブルとそのすべての非クラスター化インデックスについて、物理的な一貫性と論理的な一貫性の両方をチェックします。 ただし、XML インデックス、空間インデックス、およびインデックス付きビューのみに物理的な一貫性チェックが既定で実行されます。    
    -   WITH EXTENDED_LOGICAL_CHECKS が指定されている場合、インデックス付きビュー、XML インデックス、および空間インデックス (存在する場合) に対して論理チェックが実行されます。 既定では、論理的な一貫性のチェック前に物理的な一貫性がチェックされます。 NOINDEX も指定されている場合は、論理チェックのみが実行されます。    
         この論理的な一貫性のチェックでは、インデックス オブジェクトの内部インデックス テーブルが参照先のユーザー テーブルと照合されます。 行の不整合を検出するために、内部テーブルとユーザー テーブルの完全な積集合を実行する内部クエリが作成されます。 このクエリを実行するとパフォーマンスに多大な影響を及ぼす可能性があり、その進行状況は追跡できません。 したがって、物理的な破損とは無関係のインデックスの問題があると考えられる場合、またはページ レベルのチェックサムがオフになっており、列レベルのハードウェアの破損が考えられる場合にのみ、WITH EXTENDED_LOGICAL_CHECKS を指定することをお勧めします。    
    -   インデックスがフィルター選択されたインデックスである場合、DBCC CHECKDB は一貫性チェックを実行して、インデックス エントリがフィルター述語に適合していることを確認します。   
      
- SQL Server 2016 以降で、既定では高価な式の評価を避けるために保存される計算列、UDT 列、およびフィルター選択されたインデックスに追加のチェックは実行されません。 この変更は、これらのオブジェクトを含むデータベースに対する CHECKDB の期間が大幅に削減します。 ただし、これらのオブジェクトの物理的な整合性チェックを常に完了しました。 EXTENDED_LOGICAL_CHECKS オプションを指定する場合にのみ、式の評価行われます (インデックス付きビュー、XML インデックス、および空間インデックス) の存在の論理チェックだけでなく、EXTENDED_LOGICAL_CHECKS オプションの一部として。
-  互換性レベルが 90 以下で NOINDEX が指定されていない場合、DBCC CHECKTABLE は、1 つのテーブルまたはインデックス付きビューと、そのすべての非クラスター化インデックスおよび XML インデックスについて、物理的な一貫性と論理的な一貫性の両方をチェックします。 空間インデックスはサポートされません。
    
 **データベースの互換性レベルを調べる**    
[データベースの互換性レベルの表示または変更](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)    
    
## <a name="internal-database-snapshot"></a>内部データベース スナップショット    
DBCC CHECKTABLE は、内部データベースのスナップショットを使用して、これらのチェックを実行するために必要なトランザクションの一貫性を確保します。 詳細については、次を参照してください[データベース スナップショット & #40; のスパース ファイルのサイズを表示。TRANSACT-SQL と #41 です。](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) 「DBCC 内部データベース スナップショットの使用」」、および[DBCC & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-transact-sql.md).
スナップショットを作成できない場合や、TABLOCK が指定されている場合は、DBCC CHECKTABLE は共有テーブル ロックを取得して必要な一貫性を実現します。
    
> [!NOTE]    
> Tempdb に対して DBCC CHECKTABLE を実行すると、共有テーブル ロックを取得して必要があります。 これは、パフォーマンス上の理由から、データベースのスナップショットが tempdb では利用できないためです。 つまり、必要なトランザクションの一貫性を実現できないためです。    
    
## <a name="checking-and-repairing-filestream-data"></a>FILESTREAM データのチェックと修復    
データベースとテーブルの FILESTREAM が有効になって、必要に応じて保存できます**varbinary (max)**ファイル システム内のバイナリ ラージ オブジェクト (Blob)。 BLOB をファイル システムに格納するテーブルに対して DBCC CHECKTABLE を使用する場合は、DBCC によって、ファイル システムとデータベースの間でのリンクレベルの一貫性がチェックされます。
たとえば、テーブルが含まれている場合、 **varbinary (max)** DBCC CHECKTABLE、FILESTREAM 属性を使用する列はファイル システムのディレクトリおよびファイルとテーブルの行、列、および列の間の一対一のマッピングがあることを確認値。 REPAIR_ALLOW_DATA_LOSS オプションを指定すると、DBCC CHECKTABLE で破損を修復できます。 FILESTREAM の破損を修復するため、DBCC はファイル システム データがないテーブル行をすべて削除し、テーブルの行、列、および列の値にマップされないディレクトリとファイルをすべて削除します。
    
## <a name="checking-objects-in-parallel"></a>オブジェクトの並列チェック    
既定では、DBCC CHECKTABLE はオブジェクトの並列チェックを実行します。 並列処理の次数は、クエリ プロセッサによって自動的に決定されます。 並列処理の最大限度は、並列クエリと同様に構成します。 使用して DBCC チェックに利用できるプロセッサの最大数を制限するには、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。
並列チェックはトレース フラグ 2528 を使用して無効にできます。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」を参照してください。
    
> [!NOTE]    
>  DBCC CHECKTABLE の操作中、バイト順のユーザー定義型の列に保存されるバイトは、シリアル化されたユーザー定義型の計算値と同じである必要があります。 同じでない場合は、DBCC CHECKTABLE ルーチンで一貫性エラーが報告されます。    
    
## <a name="understanding-dbcc-error-messages"></a>DBCC エラー メッセージについて    
メッセージが書き込まれます DBCC CHECKTABLE コマンドの終了後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログ。 DBCC コマンドが正常に実行された場合、メッセージでは正常完了とコマンド実行時間が示されます。 エラーのため、チェックを完了する前に、DBCC コマンドが停止すると、メッセージは、コマンドが終了した、状態の値とコマンド実行時間の量を示します。 次の表は、メッセージに含まれる可能性がある状態値の一覧と説明です。
    
|状態|Description|    
|-----------|-----------------|    
|0|エラー番号 8930 が発生しました。 メタデータの破損が原因で DBCC コマンドが終了しました。|    
|1|エラー番号 8967 が発生しました。 内部 DBCC エラーがあります。|    
|2|緊急モードのデータベース修復中にエラーが発生しました。|    
|3|メタデータの破損が原因で DBCC コマンドが終了しました。|    
|4|アサートまたはアクセス違反が検出されました。|    
|5|不明なエラーが発生し、DBCC コマンドが終了しました。|    
    
## <a name="error-reporting"></a>[エラー報告]    
ミニ ダンプ ファイル (SQLDUMP*nnnn*.txt) で作成された、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBCC CHECKTABLE で破損エラーが検出されるたびに、ログ ディレクトリ。 インスタンスの機能の使用状況データ収集およびエラー レポート機能が有効な場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、ファイルが自動的に転送[!INCLUDE[msCoName](../../includes/msconame-md.md)]です。 収集されたデータは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能向上のために使用されます。
このダンプ ファイルには、DBCC CHECKTABLE コマンドの結果と追加の診断出力が含まれます。 また、制限付きの随意アクセス制御リスト (DACL) が割り当てられます。 アクセスが制限されて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントと sysadmin ロールのメンバーです。 既定では、sysadmin ロールには、Windows の builtin \administrators グループとローカルの管理者のグループのすべてのメンバーが含まれています。 データ収集プロセスが失敗しても、DBCC コマンドは失敗しません。
    
## <a name="resolving-errors"></a>エラーの解決    
 DBCC CHECKTABLE でエラーが報告された場合は、REPAIR オプションのいずれかを指定して実行するのではなく、データベースのバックアップからデータベースを復元することをお勧めします。 バックアップが存在しない場合は、REPAIR を実行することによって、報告されたエラーを修正できます。 使用する REPAIR オプションは、報告されたエラーの一覧の最後に指定されています。 ただし、REPAIR_ALLOW_DATA_LOSS オプションを使用して、エラーを修正することには、ページとそのため、データを削除する必要があります。    
ユーザー トランザクションを利用して修復を実行できるので、後からユーザーが変更をロールバックすることができます。 修復をロールバックしたときは、データベースにエラーが残っているので、データベースをバックアップから復元する必要があります。 すべての修復が完了したら、データベースをバックアップします。
    
## <a name="result-sets"></a>結果セット    
DBCC CHECKTABLE は次の結果セットを返します。 テーブル名のみを指定した場合もその他のオプションを指定した場合も、同じ結果セットを返します。
    
```sql
DBCC results for 'HumanResources.Employee'.    
There are 288 rows in 13 pages for object 'Employee'.    
DBCC execution completed. If DBCC printed error messages, contact your system administrator.    
```    
    
ESTIMATEONLY オプションを指定した場合、DBCC CHECKTABLE は次の結果セットを返します。
    
```sql
Estimated TEMPDB space needed for CHECKTABLES (KB)     
--------------------------------------------------     
21    
(1 row(s) affected)    
DBCC execution completed. If DBCC printed error messages, contact your system administrator.    
```    
    
## <a name="permissions"></a>Permissions    
ユーザーは、テーブルを所有する必要がありますか、sysadmin 固定サーバー ロールのメンバーである、db_owner 固定データベース ロール、または db_ddladmin 固定データベース ロール。    
    
## <a name="examples"></a>使用例    
    
### <a name="a-checking-a-specific-table"></a>A. 特定のテーブルをチェックする    
次の例のデータ ページの整合性の確認、`HumanResources.Employee`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。
    
```sql    
DBCC CHECKTABLE ('HumanResources.Employee');    
GO    
```    
    
### <a name="b-performing-a-low-overhead-check-of-the-table"></a>B. テーブルの低オーバーヘッド チェックを実行する    
 次の例の低オーバーヘッド チェックを実行する、`Employee`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。    
    
```sql    
DBCC CHECKTABLE ('HumanResources.Employee') WITH PHYSICAL_ONLY;    
GO    
```    
    
### <a name="c-checking-a-specific-index"></a>C. 特定のインデックスをチェックする    
 次の例では、特定のインデックスにアクセスして取得した`sys.indexes`です。    
    
```sql    
DECLARE @indid int;    
SET @indid = (SELECT index_id     
              FROM sys.indexes    
              WHERE object_id = OBJECT_ID('Production.Product')    
                    AND name = 'AK_Product_Name');    
DBCC CHECKTABLE ('Production.Product',@indid);    
```    
    
## <a name="see-also"></a>参照    
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)    
    
  

