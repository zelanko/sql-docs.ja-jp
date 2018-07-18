---
title: DECLARE CURSOR (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECLARE_CURSOR_TSQL
- CURSOR_TSQL
- DECLARE CURSOR
- CURSOR
dev_langs:
- TSQL
helpviewer_keywords:
- DECLARE CURSOR statement
- cursors [SQL Server], attributes
- local cursors [SQL Server]
- nesting cursors
- Transact-SQL cursors, attributes
- global cursors [SQL Server]
ms.assetid: 5a3a27aa-03e8-4c98-a27e-809282379b21
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 82a1ce7e2b416ed0b31b6612d580e95ac7d7500e
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36242114"
---
# <a name="declare-cursor-transact-sql"></a>DECLARE CURSOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルの属性を定義します。これには、スクロール動作や、カーソルが操作する結果セットを作成するクエリなどが含まれます。 DECLARE CURSOR は、ISO 標準に基づく構文と、[!INCLUDE[tsql](../../includes/tsql-md.md)] の拡張機能のセットを使用する構文の両方で指定できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ISO Syntax  
DECLARE cursor_name [ INSENSITIVE ] [ SCROLL ] CURSOR   
     FOR select_statement   
     [ FOR { READ ONLY | UPDATE [ OF column_name [ ,...n ] ] } ]  
[;]  
Transact-SQL Extended Syntax  
DECLARE cursor_name CURSOR [ LOCAL | GLOBAL ]   
     [ FORWARD_ONLY | SCROLL ]   
     [ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]   
     [ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]   
     [ TYPE_WARNING ]   
     FOR select_statement   
     [ FOR UPDATE [ OF column_name [ ,...n ] ] ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *cursor_name*  
 定義された [!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルの名前です。 *cursor_name* は識別子の規則に準拠している必要があります。  
  
 INSENSITIVE  
 データの一時コピーを作成するためのカーソルを定義します。作成されるコピーは、カーソルで使用されます。 このカーソルに対する要求の応答は、すべて **tempdb** 内のこの一時テーブルから得られます。したがって、ベース テーブルへの修正は、このカーソルで取り出したデータには反映されません。また、このカーソルで修正を行うこともできません。 ISO 構文で INSENSITIVE を指定しない場合は、任意のユーザーによって基になるテーブルに加えられた削除および更新がコミットされると、以降のフェッチで反映されます。  
  
 SCROLL  
 すべてのフェッチ オプション (FIRST、LAST、PRIOR、NEXT、RELATIVE、ABSOLUTE) が利用できることを指定します。 ISO 形式の DECLARE CURSOR ステートメントに SCROLL を指定しない場合は、NEXT フェッチ オプションだけがサポートされます。 FAST_FORWARD も指定した場合は、SCROLL を指定できません。  
  
 *select_statement*  
 カーソルの結果セットを定義する標準の SELECT ステートメントです。 カーソル宣言の *select_statement* 内で FOR BROWSE および INTO キーワードは許可されません。  
  
 *select_statement* 内の句が、要求されたカーソルの種類の機能と矛盾する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってカーソルが別の種類に暗黙的に変換されます。  
  
 READ ONLY  
 このカーソルによる更新を禁止します。 UPDATE または DELETE ステートメントの WHERE CURRENT OF 句で、このカーソルを参照することはできません。 このオプションは、更新対象のカーソルの既定の機能をオーバーライドします。  
  
 UPDATE [OF *column_name* [**,**...*n*]]  
 カーソル内で更新できる列を定義します。 OF *column_name* [**,**..*.n*] を指定した場合は、指定した列に対してのみ更新ができます。 列リストを伴わずに UPDATE を指定した場合は、すべての列を更新できます。  
  
 *cursor_name*  
 定義された [!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルの名前です。 *cursor_name* は識別子の規則に準拠している必要があります。  
  
 LOCAL  
 カーソルのスコープは、カーソルが作成されたバッチ、ストアド プロシージャ、またはトリガーに対してローカルです。 カーソル名は、そのスコープの中でだけ有効です。 カーソルは、バッチ、ストアド プロシージャ、またはトリガー内のローカル カーソル変数からか、ストアド プロシージャの OUTPUT パラメーターから参照できます。 OUTPUT パラメーターは、呼び出し側のバッチ、ストアド プロシージャ、トリガーにローカル カーソルを戻すのに使用されます。呼び出し側はパラメーターをカーソル変数に割り当て、ストアド プロシージャが終了した後でカーソルを参照できます。 カーソルは、OUTPUT パラメーターで戻された場合を除いて、バッチ、ストアド プロシージャ、またはトリガーが終了するときに暗黙的に割り当てを解除されます。 OUTPUT パラメーターで戻された場合は、カーソルを参照している最後の変数の割り当てが解除されるか、そのスコープが失われたときに、カーソルの割り当てが解除されます。  
  
 GLOBAL  
 カーソルのスコープは、接続に対してグローバルです。 カーソル名は、その接続によって実行されるストアド プロシージャやバッチの中で参照できます。 カーソルは、切断のときだけ暗黙的に割り当てを解除されます。  
  
> [!NOTE]  
>  GLOBAL も LOCAL も指定しない場合は、**default to local cursor** データベース オプションの設定によって既定の動作が決まります。  
  
 FORWARD_ONLY  
 カーソルが先頭行から最終行に向かってだけスクロールできることを指定します。 FETCH NEXT は、サポートされている唯一のフェッチ オプションです。 STATIC、KEYSET、または DYNAMIC キーワードを伴わずに FORWARD_ONLY を指定した場合、カーソルは DYNAMIC カーソルとして動作します。 FORWARD_ONLY も SCROLL も指定しなかった場合は、STATIC、KEYSET、または DYNAMIC キーワードを指定しない限り、FORWARD_ONLY が既定値になります。 STATIC、KEYSET、および DYNAMIC カーソルは、特に指定のない限り SCROLL に設定されます。 ODBC や ADO などのデータベース API と異なり、FORWARD_ONLY は、STATIC、KEYSET、および DYNAMIC [!INCLUDE[tsql](../../includes/tsql-md.md)] カーソルでサポートされます。  
  
 STATIC  
 データの一時コピーを作成するためのカーソルを定義します。作成されるコピーは、カーソルで使用されます。 このカーソルに対する要求の応答は、すべて **tempdb** 内のこの一時テーブルから得られます。したがって、ベース テーブルへの修正は、このカーソルで取り出したデータには反映されません。また、このカーソルで修正を行うこともできません。  
  
 KEYSET  
 カーソルを開くときに、カーソル内の行の構成要素と順序が固定されることを指定します。 行を一意に識別するキーのセットは、**tempdb** 内の **keyset** というテーブルに組み込まれています。  
  
> [!NOTE]  
>  クエリが一意なインデックスのないテーブルを少なくとも 1 つ参照する場合、このキーセット カーソルは静的カーソルに変換されます。  
  
 ベース テーブル内の非キー値がカーソル所有者によって変更されるか、変更が他のユーザーによってコミットされると、その変更は、所有者がカーソルの周囲をスクロールするときに表示されます。 他のユーザーによって行われた挿入は表示されません ([!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルを介して、挿入を行うことはできません)。 行が削除された場合に、その行をフェッチしようとすると、@@FETCH_STATUS が -2 に設定されて返されます。 カーソル外部からキー値を更新すると、古い行を削除した後で新しい行を挿入した場合と同様に、 新しい値の行は表示されず、古い値の行をフェッチしようとすると @@FETCH_STATUS が -2 に設定されて返されます。 新しい値は、WHERE CURRENT OF 句を指定してカーソルから更新を終了した場合に表示されます。  
  
 DYNAMIC  
 カーソルの周囲をスクロールするときに、結果セット内の行に対して行ったすべてのデータ変更を反映するカーソルを定義します。 行のデータ値、順序、構成要素は、各フェッチ操作で変化する可能性があります。 ABSOLUTE フェッチ オプションは、動的カーソルではサポートされません。  
  
 FAST_FORWARD  
 パフォーマンスの最適化が有効に設定された FORWARD_ONLY、READ_ONLY カーソルを指定します。 SCROLL または FOR_UPDATE も指定した場合は、FAST_FORWARD を指定できません。  
  
> [!NOTE]  
>  FAST_FORWARD と FORWARD_ONLY の両方を同じ DECLARE CURSOR ステートメントで使用できます。  
  
 READ_ONLY  
 このカーソルによる更新を禁止します。 UPDATE または DELETE ステートメントの WHERE CURRENT OF 句で、このカーソルを参照することはできません。 このオプションは、更新対象のカーソルの既定の機能をオーバーライドします。  
  
 SCROLL_LOCKS  
 カーソルによって行われる位置指定更新または位置指定削除の成功が保証されることを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はカーソルに読み取られた行をロックし、後で変更できることを保証します。 FAST_FORWARD または STATIC も指定した場合は、SCROLL_LOCKS を指定できません。  
  
 OPTIMISTIC  
 行がカーソルに読み取られてから更新された場合に、カーソルによって行われる位置指定更新または位置指定削除が失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、行がカーソルに読み取られるとき、その行はロックされません。 代わりに **timestamp** 列の値を比較するか、テーブルに **timestamp** 列がない場合はチェックサム値を使用して、行がカーソルに読み込まれてから変更されたかどうかが判別されます。 行が変更されている場合、位置指定更新または位置指定削除の試行は失敗します。 FAST_FORWARD を指定した場合は、OPTIMISTIC を指定できません。  
  
 TYPE_WARNING  
 カーソルの種類が、要求されたものから別のものに暗黙的に変換された場合、クライアントに警告メッセージが送信されます。  
  
 *select_statement*  
 カーソルの結果セットを定義する標準の SELECT ステートメントです。 COMPUTE、COMPUTE BY、FOR BROWSE、および INTO キーワードは、カーソル宣言の *select_statement* で使用することはできません。  
  
> [!NOTE]  
>  カーソル宣言内ではクエリ ヒントを使用できますが、FOR UPDATE OF 句も使用する場合は、FOR UPDATE OF の後に OPTION (*query_hint*) を指定する必要があります。  
  
 *select_statement* 内の句が、要求されたカーソルの種類の機能と矛盾する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってカーソルが別の種類に暗黙的に変換されます。 詳細については、「暗黙的なカーソル変換」を参照してください。  
  
 FOR UPDATE [OF *column_name* [**,**...*n*]]  
 カーソル内で更新できる列を定義します。 OF *column_name* [**,**...*n*] を指定した場合は、指定した列に対してのみ更新ができます。 列リストを伴わずに UPDATE を指定した場合は、すべての列を更新できます。ただし、READ_ONLY 同時実行オプションを指定した場合は除きます。  
  
## <a name="remarks"></a>Remarks  
 DECLARE CURSOR は、[!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルの属性を定義します。これには、スクロール動作や、カーソルが操作する結果セットを作成するクエリなどが含まれます。 OPEN ステートメントは結果セットを設定し、FETCH ステートメントは結果セットから行を返します。 CLOSE ステートメントは、カーソルに関係付けられた現在の結果セットを解放します。 DEALLOCATE ステートメントは、カーソルが使用するリソースを解放します。  
  
 最初の形式の DECLARE CURSOR ステートメントは、ISO 構文を使用してカーソルの動作を宣言します。 2 番目の形式の DECLARE CURSOR は、[!INCLUDE[tsql](../../includes/tsql-md.md)] の拡張機能を使用します。これによって、ODBC または ADO のデータベース API カーソル関数で使用されるカーソルの種類と同じカーソルの種類を使用して、カーソルを定義できます。  
  
 2 つの形式を混在することはできません。 CURSOR キーワードの前に SCROLL または INSENSITIVE キーワードを指定した場合、CURSOR キーワードと FOR *select_statement* キーワードの間で一切のキーワードを使用できません。 CURSOR キーワードと FOR *select_statement* キーワードの間でキーワードを指定した場合、CURSOR キーワードの前に SCROLL または INSENSITIVE キーワードを指定できません。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文を使用する DECLARE CURSOR が READ_ONLY、OPTIMISTIC、または SCROLL_LOCKS を指定しない場合、既定値は次のとおりです。  
  
-   権限が十分でなかったり、更新をサポートしないリモート テーブルにアクセスしているなどの理由で、SELECT ステートメントが更新をサポートしない場合、カーソルは READ_ONLY です。  
  
-   STATIC および FAST_FORWARD カーソルの既定値は READ_ONLY です。  
  
-   DYNAMIC および KEYSET カーソルの既定値は OPTIMISTIC です。  
  
 カーソル名は、他の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでのみ参照できます。 データベース API 関数でカーソル名を参照することはできません。 たとえば、カーソルの宣言後、OLE DB、ODBC、または ADO 関数やメソッドからカーソル名を参照することはできません。 カーソル行は、フェッチ関数や API のメソッドでフェッチすることはできません。[!INCLUDE[tsql](../../includes/tsql-md.md)] FETCH ステートメントによってのみフェッチできます。  
  
 カーソルの宣言後、次に示すシステム ストアド プロシージャを使用すると、カーソルの特性を判断できます。  
  
|システム ストアド プロシージャ|[説明]|  
|------------------------------|-----------------|  
|**sp_cursor_list**|現在接続時に可視であるカーソルとその属性の一覧を返します。|  
|**sp_describe_cursor**|順方向専用カーソルか、スクロール カーソルかなど、カーソルの属性を記述します。|  
|**sp_describe_cursor_columns**|カーソル結果セット内の列の属性を記述します。|  
|**sp_describe_cursor_tables**|カーソルがアクセスするベース テーブルを記述します。|  
  
 カーソルを宣言する *select_statement* の一部として、変数を使用できます。 カーソルが宣言された後、カーソル変数の値は変更されません。  
  
## <a name="permissions"></a>アクセス許可  
 DECLARE CURSOR 権限は、特に指定のない限りカーソル内で使用されるビュー、テーブル、および列の SELECT 権限を持つユーザーに与えられます。
 
## <a name="limitations-and-restrictions"></a>制限事項と制約事項

クラスター化列ストア インデックスを使用しているテーブルでは、カーソルやトリガーは使用できません。 この制限は、非クラスター化列ストア インデックスには適用されません。非クラスター化列ストア インデックスを使用しているテーブルでは、カーソルとトリガーを使用できます。 
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-simple-cursor-and-syntax"></a>A. 単純なカーソルと構文を使用する  

このカーソルのオープン時に作成された結果セットには、テーブルに存在するすべての行と列が含まれています。 このカーソルは更新することができ、すべての更新結果および削除結果は、このカーソルに対して行ったフェッチに反映されます。 `SCROLL` オプションを指定していないため、フェッチに使用できるのは `FETCH NEXT` のみです。  

  
```  
DECLARE vend_cursor CURSOR  
    FOR SELECT * FROM Purchasing.Vendor  
OPEN vend_cursor  
FETCH NEXT FROM vend_cursor;  
```  
  
### <a name="b-using-nested-cursors-to-produce-report-output"></a>B. 入れ子になったカーソルを使用してレポート出力を作成する  
 次の例では、カーソルを入れ子にして複雑なレポートを作成する方法を示します。 内部のカーソルは、各製造元に対して宣言されます。  
  
```  
SET NOCOUNT ON;  
  
DECLARE @vendor_id int, @vendor_name nvarchar(50),  
    @message varchar(80), @product nvarchar(50);  
  
PRINT '-------- Vendor Products Report --------';  
  
DECLARE vendor_cursor CURSOR FOR   
SELECT VendorID, Name  
FROM Purchasing.Vendor  
WHERE PreferredVendorStatus = 1  
ORDER BY VendorID;  
  
OPEN vendor_cursor  
  
FETCH NEXT FROM vendor_cursor   
INTO @vendor_id, @vendor_name  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    PRINT ' '  
    SELECT @message = '----- Products From Vendor: ' +   
        @vendor_name  
  
    PRINT @message  
  
    -- Declare an inner cursor based     
    -- on vendor_id from the outer cursor.  
  
    DECLARE product_cursor CURSOR FOR   
    SELECT v.Name  
    FROM Purchasing.ProductVendor pv, Production.Product v  
    WHERE pv.ProductID = v.ProductID AND  
    pv.VendorID = @vendor_id  -- Variable value from the outer cursor  
  
    OPEN product_cursor  
    FETCH NEXT FROM product_cursor INTO @product  
  
    IF @@FETCH_STATUS <> 0   
        PRINT '         <<None>>'       
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
  
        SELECT @message = '         ' + @product  
        PRINT @message  
        FETCH NEXT FROM product_cursor INTO @product  
        END  
  
    CLOSE product_cursor  
    DEALLOCATE product_cursor  
        -- Get the next vendor.  
    FETCH NEXT FROM vendor_cursor   
    INTO @vendor_id, @vendor_name  
END   
CLOSE vendor_cursor;  
DEALLOCATE vendor_cursor;  
```  
  
## <a name="see-also"></a>参照  
 [@@FETCH_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/fetch-status-transact-sql.md)   
 [CLOSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [カーソル &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DEALLOCATE &#40;Transact-SQL&#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
