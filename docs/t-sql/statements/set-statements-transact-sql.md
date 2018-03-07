---
title: "SET ステートメント (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET
- SET_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ISO SET statements
- queries [SQL Server], executing
- dates [SQL Server], SET statements
- time [SQL Server], SET statements
- SET statement, about SET statement
- SET statement
- statistical information [SQL Server], SET statements
- locking [SQL Server], SET statements
ms.assetid: f7e107f8-0fcf-408b-b30f-da2323eeb714
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 3832a2be6952354122c999d3c88c7ad1610b623d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-statements-transact-sql"></a>SET ステートメント (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] プログラミング言語には、現在のセッションにおける特定の情報の処理方法を変更する SET ステートメントがいくつか用意されています。 これらの SET ステートメントは、次の表に示すカテゴリに分類されます。  
  
 SET ステートメントでローカル変数の設定については、次を参照してください。[設定@local_variable&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
|カテゴリ|ステートメント|  
|--------------|----------------|  
|日付時刻ステートメント|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)<br /><br /> [DATEFORMAT の設定](../../t-sql/statements/set-dateformat-transact-sql.md)|  
|ロック ステートメント|[SET DEADLOCK_PRIORITY](../../t-sql/statements/set-deadlock-priority-transact-sql.md)<br /><br /> [[SET LOCK_TIMEOUT]](../../t-sql/statements/set-lock-timeout-transact-sql.md)|  
|その他のステートメント|[セット CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)<br /><br /> [[SET CURSOR_CLOSE_ON_COMMIT]](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)<br /><br /> [SET FIPS_FLAGGER](../../t-sql/statements/set-fips-flagger-transact-sql.md)<br /><br /> [SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)<br /><br /> [言語を設定します。](../../t-sql/statements/set-language-transact-sql.md)<br /><br /> [セット オフセット](../../t-sql/statements/set-offsets-transact-sql.md)<br /><br /> [[SET QUOTED_IDENTIFIER]](../../t-sql/statements/set-quoted-identifier-transact-sql.md)|  
|クエリ実行ステートメント|[[SET ARITHABORT]](../../t-sql/statements/set-arithabort-transact-sql.md)<br /><br /> [SET ARITHIGNORE](../../t-sql/statements/set-arithignore-transact-sql.md)<br /><br /> [SET FMTONLY](../../t-sql/statements/set-fmtonly-transact-sql.md)<br /><br /> 注:[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> [[SET NOCOUNT]](../../t-sql/statements/set-nocount-transact-sql.md)<br /><br /> [[SET NOEXEC]](../../t-sql/statements/set-noexec-transact-sql.md)<br /><br /> [SET NUMERIC_ROUNDABORT](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)<br /><br /> [[SET PARSEONLY]](../../t-sql/statements/set-parseonly-transact-sql.md)<br /><br /> [[SET QUERY_GOVERNOR_COST_LIMIT]](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)<br /><br /> [[SET ROWCOUNT]](../../t-sql/statements/set-rowcount-transact-sql.md)<br /><br /> [[SET TEXTSIZE]](../../t-sql/statements/set-textsize-transact-sql.md)|  
|ISO 設定ステートメント|[[SET ANSI_DEFAULTS]](../../t-sql/statements/set-ansi-defaults-transact-sql.md)<br /><br /> [セット ANSI_NULL_DFLT_OFF](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)<br /><br /> [セット ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)<br /><br /> [[SET ANSI_NULLS]](../../t-sql/statements/set-ansi-nulls-transact-sql.md)<br /><br /> [[SET ANSI_PADDING]](../../t-sql/statements/set-ansi-padding-transact-sql.md)<br /><br /> [[SET ANSI_WARNINGS]](../../t-sql/statements/set-ansi-warnings-transact-sql.md)|  
|統計ステートメント|[SET FORCEPLAN](../../t-sql/statements/set-forceplan-transact-sql.md)<br /><br /> [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)<br /><br /> [[SET SHOWPLAN_TEXT]](../../t-sql/statements/set-showplan-text-transact-sql.md)<br /><br /> [SET SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md)<br /><br /> [SET STATISTICS IO](../../t-sql/statements/set-statistics-io-transact-sql.md)<br /><br /> [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)<br /><br /> [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)<br /><br /> [SET STATISTICS TIME](../../t-sql/statements/set-statistics-time-transact-sql.md)|  
|トランザクション ステートメント|[[SET IMPLICIT_TRANSACTIONS]](../../t-sql/statements/set-implicit-transactions-transact-sql.md)<br /><br /> [SET REMOTE_PROC_TRANSACTIONS](../../t-sql/statements/set-remote-proc-transactions-transact-sql.md)<br /><br /> [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)<br /><br /> [SET XACT_ABORT](../../t-sql/statements/set-xact-abort-transact-sql.md)|  
  
## <a name="considerations-when-you-use-the-set-statements"></a>SET ステートメントの使用に関する注意点  
  
-   SET FIPS_FLAGGER、SET OFFSETS、SET PARSEONLY、SET QUOTED_IDENTIFIER を除くすべての SET ステートメントは、実行時に実装されます。 SET FIPS_FLAGGER、SET OFFSETS、SET PARSEONLY、SET QUOTED_IDENTIFIER ステートメントは解析時に実装されます。  
  
-   SET ステートメントをストアド プロシージャまたはトリガー内で実行した場合、SET オプションの値は、ストアド プロシージャやトリガーから制御が返された後、元に戻されます。 また、動的 SQL 文字列を使用して実行するには SET ステートメントが指定されている場合**sp_executesql**または動的 SQL 文字列に指定されたバッチから制御が返された後に実行"、"SET オプションの値を復元します。  
  
-   ストアド プロシージャでは、SET ANSI_NULLS と SET QUOTED_IDENTIFIERS を除き、実行時に指定した SET 設定が使用されます。 SET ANSI_NULLS または SET QUOTED_IDENTIFIER を指定するストアド プロシージャの場合は、ストアド プロシージャの作成時に指定した設定が使用されます。 ストアド プロシージャの内部で使用する場合、SET 設定は無視されます。  
  
-   **ユーザー オプション**設定**sp_configure**では、サーバー全体の設定と、複数のデータベース間で機能します。 この設定は明示的な SET ステートメントと同じように動作しますが、ログイン時に使用される点が異なります。  
  
-   ALTER DATABASE を使用して設定したデータベース設定は、データベース レベルで有効です。これは明示的に設定された場合のみ有効になります。 データベースの設定を使用して設定されているインスタンス オプションの設定をオーバーライドする**sp_configure**です。  
  
-   ON と OFF を設定できる SET ステートメントでは、複数の SET オプションに対して一度に ON または OFF を設定できます。  
  
    > [!NOTE]  
    >  ただしこれは、統計情報に関連する SET オプションでは適用されません。  
  
     たとえば、 `SET QUOTED_IDENTIFIER, ANSI_NULLS ON` QUOTED_IDENTIFIER と ANSI_NULLS の両方を ON に設定します。  
  
-   SET ステートメントの設定は、ALTER DATABASE を使用して設定した同等のデータベース オプションの設定よりも優先されます。 たとえば、SET ANSI_NULLS ステートメントで指定した値は、ANSI_NULLS のデータベース設定よりも優先されます。 さらに、いくつかの接続設定が自動的に設定で、ユーザーが以前を使用して有効になる値に基づき、データベースに接続するとき、 **sp_configure ユーザー オプション**設定、またはすべての ODBC に適用される値とOLE/DB 接続です。  
  
-   ALTER、CREATE、および DROP DATABASE ステートメントでは、SET LOCK_TIMEOUT の設定は無視されます。  
  
-   SET ANSI_DEFAULTS などのグローバルまたはショートカット SET ステートメントでいくつかの設定を行っている場合、ショートカット SET ステートメントを実行すると、そのショートカット SET ステートメントの影響を受けるすべてのオプションに関する既存の設定がリセットされます。 ショートカット SET ステートメントを実行した後、ショートカット SET ステートメントの影響を受ける SET オプションを個別に明示的に設定した場合は、個別の SET ステートメントの値の方が、対応するショートカットの設定よりも優先されます。  
  
-   バッチを使用する場合、データベースのコンテキストは、USE ステートメントを使って確立したバッチによって決まります。 ストアド プロシージャの外部で実行される、バッチ内のアドホック クエリとその他すべてのステートメントは、USE ステートメントによって確立されるデータベースと接続のオプション設定を継承します。  
  
-   複数のアクティブな結果セット (MARS) 要求では、グローバル状態が共有されます。この状態には、最新のセッションでの SET オプション設定が含まれます。 各要求を実行するとき、SET オプションを変更できます。 この変更は対象となる要求のコンテキストだけに適用され、同時実行される他の MARS 要求には影響しませんが、 要求の実行が完了した後に、新しい SET オプションがグローバル セッション状態にコピーされます。 この変更後、同じセッションで実行される新しい要求では、これらの新しい SET オプション設定が使用されます。  
  
-   バッチまたは他のストアド プロシージャから実行されるストアド プロシージャでは、そのストアド プロシージャが格納されているデータベースに現在設定されているオプション値が使用されます。 たとえば、格納されているときにプロシージャ**db1.dbo.sp1**ストアド プロシージャを呼び出す**db2.dbo.sp2**、ストアド プロシージャ**sp1**が現在の互換性レベルで実行データベースの設定**db1**、ストアド プロシージャと**sp2**データベースの現在の互換性レベル設定で実行される**db2**です。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで複数のデータベースにあるオブジェクトを参照するときには、現在のデータベース コンテキストと現在の接続コンテキストがステートメントに適用されます。 この例では場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントがバッチでは、現在の接続コンテキストには、使用するステートメントで定義されたデータベースがある場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントがストアド プロシージャでは、接続コンテキストは、ストアド プロシージャを含むデータベース。  
  
-   計算列またはインデックス付きビューでインデックスを作成または操作する場合は、SET オプションの ARITHABORT、CONCAT_NULL_YIELDS_NULL、QUOTED_IDENTIFIER、ANSI_NULLS、ANSI_PADDING、および ANSI_WARNINGS を ON に設定する必要があります。 NUMERIC_ROUNDABORT オプションは OFF に設定する必要があります。  
  
     これらのオプションのうち 1 つでも正しく設定しなかった場合は、インデックス付きビューに対して、または計算列にインデックスが含まれているテーブルに対して INSERT、UPDATE、DELETE、DBCC CHECKDB、および DBCC CHECKTABLE を実行すると操作は失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではエラーが発生し、正しく設定されなかったすべてのオプションが一覧表示されます。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このようなテーブルやインデックス付きビューに対して SELECT ステートメントを実行すると、計算列またはビューにインデックスが存在しないものとして処理されます。  
  
  
