---
title: "シーケンス (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SEQUENCE
- CREATE SEQUENCE
- SEQUENCE_TSQL
- CREATE_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE SEQUENCE statement
- sequence number object, creating
- sequence object
- number, sequence
ms.assetid: 419f907b-8a72-4d6c-80cb-301df44c24c1
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 89a96d101c17f528b9ff14ca523e5dc41ada2f4c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-sequence-transact-sql"></a>CREATE SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  シーケンス オブジェクトを作成し、そのプロパティを指定します。 シーケンスは、シーケンスが作成された仕様に従って数値のシーケンスを生成するユーザー定義のスキーマ バインド オブジェクトです。 数値のシーケンスは、定義された間隔で昇順または降順に生成され、要求に応じて再起動 (繰り返し) するように構成できます。 ID 列とは異なり、シーケンスは、特定のテーブルに関連付けられていません。 アプリケーションは、シーケンス オブジェクトを参照して、次の値を受け取ります。 シーケンスとテーブルの関係は、アプリケーションによって制御されます。 ユーザー アプリケーションは、シーケンス オブジェクトを参照し、複数の行とテーブル間で値を調整できます。  
  
 行が挿入されるときに生成される id 列値とは異なり、アプリケーションは、呼び出すことによって、行を挿入せず、次のシーケンス番号を取得する、 [NEXT VALUE FOR 関数](../../t-sql/functions/next-value-for-transact-sql.md)です。 一度に複数のシーケンス番号を取得するには、 [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md) を使用します。  
  
 **CREATE SEQUENCE** および **NEXT VALUE FOR** 関数を両方使用する場合の詳細およびシナリオについては、「 [シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)」をご覧ください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE SEQUENCE [schema_name . ] sequence_name  
    [ AS [ built_in_integer_type | user-defined_integer_type ] ]  
    [ START WITH <constant> ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE [ <constant> ] } | { NO MINVALUE } ]  
    [ { MAXVALUE [ <constant> ] } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *sequence_name*  
 データベースに認識されるシーケンスの一意な名前を指定します。 種類は**sysname**です。  
  
 [ built_in_integer_type | user-defined_integer_type  
 シーケンスを任意の整数型として定義できます。 次の型を使用できます。  
  
-   **tinyint** -0 ~ 255 の範囲  
  
-   **smallint** --32,768 ~ 32,767 の範囲  
  
-   **int** --2,147, 483,648 ~ 2,147, 483,647 の範囲  
  
-   **bigint** -範囲 9,223,372,036,854,775,807 に-9,223,372,036,854,775,808  
  
-   **10 進**と**数値**小数点以下桁数は 0 です。  
  
-   許可される型のいずれかに基づくユーザー定義データ型 (別名型)。  
  
 データ型が指定されていない場合、 **bigint**データ型は既定値として使用します。  
  
 START WITH\<定数 >  
 シーケンス オブジェクトによって返される最初の値。 **開始**値のおよび最大よりも大きい値を小さい値にするかには、シーケンス オブジェクトの最小値と等しく必要があります。 新しいシーケンス オブジェクトの既定の開始値は、昇順のシーケンス オブジェクトの最小値および降順のシーケンス オブジェクトの最大値です。  
  
 インクリメントで\<定数 >  
 インクリメント (または負の場合は減少) に使用される値に対する各呼び出しのシーケンス オブジェクトの値、 **NEXT VALUE FOR**関数。 増分値が負の値の場合はシーケンス オブジェクトは降順で、それ以外の場合は昇順です。 0 は増分として使用できません。 新しいシーケンス オブジェクトの既定の増分値は 1 です。  
  
 [MINVALUE\<定数 > |**ありません MINVALUE** ]  
 シーケンス オブジェクトの境界を指定します。 新しいシーケンス オブジェクトの既定の最小値は、シーケンス オブジェクトのデータ型の最小値です。 これは、0 を **tinyint** データ型およびその他のすべてのデータ型の負の数。  
  
 [MAXVALUE\<定数 > |**ありません MAXVALUE**  
 シーケンス オブジェクトの境界を指定します。 新しいシーケンス オブジェクトの既定の最大値は、シーケンス オブジェクトのデータ型の最大値です。  
  
 [サイクル |**NO CYCLE** ]  
 最小値または最大値を超過した場合に、シーケンス オブジェクトを最小値 (または降順シーケンス オブジェクトの最大値) から再起動するか、例外をスローするかを指定するプロパティ。 新しいシーケンス オブジェクトの既定のサイクル オプションは、NO CYCLE です。  
  
 サイクルは、開始値からではなく最小値または最大値から再起動されることに注意してください。  
  
 [**キャッシュ**[\<定数 >] |キャッシュなし]  
 シーケンス番号を生成するのに必要なディスク IO の数を最小限に抑えることで、シーケンス オブジェクトを使用するアプリケーションのパフォーマンスが向上します。 CACHE の既定値です。  
  
 たとえば、キャッシュ サイズとして 50 を選択すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キャッシュされた 50 の個々 の値を保持しません。 現在の値とキャッシュに残っている値の数だけをキャッシュします。 これは、キャッシュを格納するために必要なメモリの量は、常にシーケンス オブジェクトのデータ型の 2 つのインスタンスと等しくなることを意味します。  
  
> [!NOTE]  
>  キャッシュ サイズを指定せずにキャッシュ オプションを有効にする場合、データベース エンジンによってサイズが選択されます。 ただし、この選択では一定のサイズが選択されるため、これに依存しないように注意してください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、予告なしにキャッシュ サイズの算出方法を変更する場合があります。  
  
 作成されたときに、**キャッシュ**オプションで、予期しないシャット ダウン (電源障害など)、失われる可能性のシーケンス番号がキャッシュに残っているのです。  
  
## <a name="general-remarks"></a>全般的な解説  
 シーケンス番号は、現在のトランザクションの範囲外で生成されます。 シーケンス番号を使用しているトランザクションがコミットまたはロールバックされるかどうかにかかわらず、シーケンス番号は使用されます。  
  
### <a name="cache-management"></a>キャッシュ管理  
 パフォーマンスを向上させるために[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって指定されたシーケンス番号の数を事前に割り当てます、**キャッシュ**引数。  
  
 たとえば、新しいシーケンスは開始値 1 とキャッシュ サイズ 15 で作成されます。 最初の値が必要な場合は、メモリから 1 ～ 15 の値を使用します。 最後にキャッシュされた値 (15) は、ディスクのシステム テーブルに書き込まれます。 15 の数値をすべて使用している場合は、次の要求 (16) でキャッシュを再度割り当てます。 最後にキャッシュされた値 (30) は、システム テーブルに書き込まれます。  
  
 場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]は 22 個の番号を使用した後に停止している、次のもので以前に保存された数の交換システム テーブルにメモリ (23) 内のシーケンス番号が書き込まれます。  
  
 SQL Server が再起動し、シーケンス番号が必要な場合、開始番号はシステム テーブル (23) から読み取られます。 15 の数 (23 ～ 38) のキャッシュ量がメモリに割り当てられ、次の非キャッシュ番号 (39) がシステム テーブルに書き込まれます。  
  
 場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]システム テーブル (39) からの読み取りの数に、電源障害などのイベント発生の異常停止、シーケンスが再開します。 任意のシーケンス番号 (ただし、ユーザーまたはアプリケーションによって要求されていない) メモリに割り当てられたは失われます。 この機能によってギャップ同じ値が発行しないで 2 回、1 つのシーケンス オブジェクトのとして定義されていない限り保証が残る可能性があります**サイクル**または手動で再起動します。  
  
 キャッシュは、現在の値 (発行された最後の値) とキャッシュに残っている値の数を追跡することによって、メモリに維持されます。 したがって、キャッシュによって使用されるメモリの量は、常にシーケンス オブジェクトのデータ型の 2 つのインスタンスと等しくなります。  
  
 キャッシュの引数に設定**NO CACHE**シーケンスを使用するたびに、システム テーブルを現在のシーケンス値を書き込みます。 これにより、ディスク アクセスが増えてパフォーマンスが低下する場合がありますが、意図しないギャップが発生する可能性は低減されます。 使用して数値が要求される場合にギャップが生じるまだ、 **NEXT VALUE FOR**または**sp_sequence_get_range**関数が、数値が使用されていないか、コミットされていないトランザクションで使用されます。  
  
 シーケンス オブジェクトを使用する場合、**キャッシュ**再起動シーケンス オブジェクトまたは変更する場合は、オプション、**インクリメント**、**サイクル**、 **MINVALUE**、**MAXVALUE**、キャッシュ サイズ プロパティ、キャッシュは、変更が行われる前に、システム テーブルに書き込まれるか。 キャッシュは、現在の値から開始して再書き込みされます (つまり、スキップされる番号はありません)。 キャッシュ サイズを変更すると、即座に反映されます。  
  
 **キャッシュされた値が使用可能なときの CACHE オプション**  
  
 次のプロセスが発生、シーケンス オブジェクトが次の値を生成するように要求されるたびに、**キャッシュ**オプションの場合は未使用に値が使用可能なシーケンス オブジェクトのメモリ内キャッシュです。  
  
1.  シーケンス オブジェクトの次の値が計算される。  
  
2.  シーケンス オブジェクトの新しい現在の値は、メモリ内で更新される。  
  
3.  計算された値は、呼び出し元のステートメントに返される。  
  
 **キャッシュを空になった場合の CACHE オプション**  
  
 [次へ] の値を生成するシーケンス オブジェクトが要求されるたびに、次のプロセスが発生した、**キャッシュ**オプションの場合は、キャッシュに達しました。  
  
1.  シーケンス オブジェクトの次の値が計算される。  
  
2.  新しいキャッシュの最後の値が計算される。  
  
3.  シーケンス オブジェクトのシステム テーブル行がロックされ、手順 2. (最後の値) で計算された値がシステム テーブルに書き込まれる。 キャッシュが空になったイベントが発生し、新しい永続化された値がユーザーに通知されます。  
  
 **NO CACHE オプション**  
  
 次のプロセスが発生、シーケンス オブジェクトが次の値を生成するように要求されるたびに、 **NO CACHE**オプション。  
  
1.  シーケンス オブジェクトの次の値が計算される。  
  
2.  シーケンス オブジェクトの新しい現在の値は、システム テーブルに書き込まれる。  
  
3.  計算された値は、呼び出し元のステートメントに返される。  
  
## <a name="metadata"></a>メタデータ  
 シーケンスの詳細については、「 [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)」を参照してください。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 SCHEMA に対する **CREATE SEQUENCE**権限、 **ALTER**権限、または **CONTROL** 権限が必要です。  
  
-   Db_owner および db_ddladmin 固定データベース ロールのメンバーは、作成、変更、およびシーケンス オブジェクトを削除することができます。  
  
-   Db_owner および db_datawriter 固定データベース ロールのメンバーは、番号を生成することによって、シーケンス オブジェクトを更新できます。  
  
 次の例では、ユーザーの AdventureWorks\Larry テストのスキーマでシーケンスを作成するためのアクセス許可を付与します。  
  
```  
GRANT CREATE SEQUENCE ON SCHEMA::Test TO [AdventureWorks\Larry]  
```  
  
 使用してシーケンス オブジェクトの所有権を譲渡することができます、 **ALTER AUTHORIZATION**ステートメントです。  
  
 シーケンスがユーザー定義のデータ型を使用している場合、シーケンスの作成者にはその型の REFERENCES 権限が必要です。  
  
### <a name="audit"></a>監査  
 監査する**CREATE SEQUENCE**、モニター、 **SCHEMA_OBJECT_CHANGE_GROUP**です。  
  
## <a name="examples"></a>使用例  
 例については、シーケンスを作成しを使用して、 **NEXT VALUE FOR**を参照してください、シーケンス番号を生成する関数[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)です。  
  
 ほとんどの次の例では、テストをという名前のスキーマでシーケンス オブジェクトを作成します。  
  
 テストのスキーマを作成するには、次のステートメントを実行します。  
  
```  
CREATE SCHEMA Test ;  
GO  
```  
  
### <a name="a-creating-a-sequence-that-increases-by-1"></a>A. 1 つずつ増加するシーケンスを作成します。  
 次の例では、Thierry は、it が使用されるたびに増加する CountBy1 をいずれかによってという名前のシーケンスを作成します。  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="b-creating-a-sequence-that-decreases-by-1"></a>B. 1 つずつ減少するシーケンスを作成する  
 次の例では、シーケンスは 0 から開始し、使用するたびに 1 つずつ減少します。  
  
```  
CREATE SEQUENCE Test.CountByNeg1  
    START WITH 0  
    INCREMENT BY -1 ;  
GO  
```  
  
### <a name="c-creating-a-sequence-that-increases-by-5"></a>C. 5 つずつ増加するシーケンスを作成する  
 次の例では、使用されるたびに 5 つずつ増加するシーケンスを作成します。  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 5  
    INCREMENT BY 5 ;  
GO  
```  
  
### <a name="d-creating-a-sequence-that-starts-with-a-designated-number"></a>D. 指定された数値から開始するシーケンスを作成する  
 テーブルをインポートした後、Thierry は最上位の ID 番号が 24,328 であることに気付きます。 Thierry には、24,329 で始まる番号を生成するシーケンスが必要です。 次のコードは 24,329 で始まり、1 ずつ増加するシーケンスを作成します。  
  
```  
CREATE SEQUENCE Test.ID_Seq  
    START WITH 24329  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="e-creating-a-sequence-using-default-values"></a>E. 既定値を使用してシーケンスを作成する  
 次の例では、既定値を使用して、シーケンスを作成します。  
  
```  
CREATE SEQUENCE Test.TestSequence ;  
```  
  
 次のステートメントを実行して、シーケンスのプロパティを確認します。  
  
```  
SELECT * FROM sys.sequences WHERE name = 'TestSequence' ;  
```  
  
 出力の一覧の一部は、既定値を示します。  
  
|||  
|-|-|  
|`start_value`|`-9223372036854775808`|  
|`increment`|`1`|  
|`mimimum_value`|`-9223372036854775808`|  
|`maximum_value`|`9223372036854775807`|  
|`is_cycling`|`0`|  
|`is_cached`|`1`|  
|`current_value`|`-9223372036854775808`|  
  
### <a name="f-creating-a-sequence-with-a-specific-data-type"></a>F. 特定のデータ型のシーケンスを作成する  
 次の例を使用してシーケンスを作成、 **smallint** -32,768 ~ 32,767 の範囲のデータ型。  
  
```  
CREATE SEQUENCE SmallSeq  
    AS smallint ;  
```  
  
### <a name="g-creating-a-sequence-using-all-arguments"></a>G. すべての引数を使用してシーケンスを作成する  
 次の例は、DecSeq を使用してという名前のシーケンスを作成、 **decimal** 0 ~ 255 の範囲を持つ、データ型。 シーケンスは 125 で始まり、数値が生成されるたびに 25 ずつ増加します。 シーケンスは、値が最大値の 200 を超える場合は繰り返すように設定されているため、最小値の 100 で再起動します。  
  
```  
CREATE SEQUENCE Test.DecSeq  
    AS decimal(3,0)   
    START WITH 125  
    INCREMENT BY 25  
    MINVALUE 100  
    MAXVALUE 200  
    CYCLE  
    CACHE 3  
;  
```  
  
 次のステートメントを実行、最初の値を参照してください。`START WITH` 125 のオプションです。  
  
```  
SELECT NEXT VALUE FOR Test.DecSeq;  
```  
  
 150、175、200 を返すように、ステートメントを 3 回実行します。  
  
 ステートメントを再度実行し、開始値が `MINVALUE` オプション (100) に戻ることを確認します。  
  
 次のコードを実行して、キャッシュ サイズを確認し、現在の値を表示します。  
  
```  
SELECT cache_size, current_value   
FROM sys.sequences  
WHERE name = 'DecSeq' ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SEQUENCE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [次の値を & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/next-value-for-transact-sql.md)   
 [シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  

