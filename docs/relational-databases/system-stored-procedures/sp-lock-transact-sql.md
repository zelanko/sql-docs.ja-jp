---
title: "sp_lock (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_lock_TSQL
- sp_lock
dev_langs: TSQL
helpviewer_keywords: sp_lock
ms.assetid: 9eaa0ec2-2ad9-457c-ae48-8da92a03dcb0
caps.latest.revision: "56"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0c3aab77a72b27d3e461ef4f68377897c5545051
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="splock-transact-sql"></a>sp_lock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ロックに関する情報をレポートします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]ロックに関する情報を取得する、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を使用して、 [sys.dm_tran_locks](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)動的管理ビュー。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_lock [ [ @spid1 = ] 'session ID1' ] [ , [@spid2 = ] 'session ID2' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@spid1 =** ] **'***session ID1***'**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]からのセッション ID 番号**sys.dm_exec_sessions**ユーザーは、これに関する情報をロックします。 *session ID1*は**int**で、既定値は NULL です。 実行**sp_who**セッションに関するプロセス情報を取得します。 場合*session ID1*が指定されていない、すべてのロックに関する情報が表示されます。  
  
 [  **@spid2 =** ] **'***セッション ID2***'**  
 もう 1 つ[!INCLUDE[ssDE](../../includes/ssde-md.md)]からのセッション ID 番号**sys.dm_exec_sessions**と同時にロックしている可能性が*session ID1*に関するユーザー情報も必要とします。 *セッション ID2*は**int**で、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 **Sp_lock**で指定したセッションによって保持されている各ロックに 1 行が結果セットに含まれています、  **@spid1** と **@spid2** パラメーター。 どちらの場合 **@spid1** も **@spid2** を指定すると、結果セットのレポート、ロックのすべてのセッションのインスタンスで現在アクティブな[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**spid**|**smallint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]ロックを要求するプロセスのセッション ID 番号。|  
|**dbid**|**smallint**|ロックが保持されているデータベースの ID 番号です。 DB_NAME() 関数を使用して、データベースを識別できます。|  
|**オブジェクト Id**|**int**|ロックが保持されているオブジェクトの ID 番号です。 関連するデータベースで OBJECT_NAME() 関数を使用して、オブジェクトを識別できます。 値 99 は、データベース内のページ割り当てを記録するために使用されるいずれかのシステム ページのロックを示す特殊な値です。|  
|**IndId**|**smallint**|ロックが保持されているインデックスの ID 番号です。|  
|**型**|**nchar(4)**|ロックの種類:<br /><br /> RID = 行識別子 (RID) で識別されるテーブル内の単一行のロック。<br /><br /> KEY = シリアル化可能なトランザクションのキーの範囲を保護するインデックス内のロック。<br /><br /> PAG = データまたはインデックス ページのロック。<br /><br /> EXT = エクステントのロック。<br /><br /> TAB = すべてのデータとインデックスを含むテーブル全体のロック。<br /><br /> DB = データベースのロック。<br /><br /> FIL = データベース ファイルのロック。<br /><br /> APP = アプリケーションで指定されたリソースのロック。<br /><br /> MD = メタデータまたはカタログ情報のロック。<br /><br /> HBT = ヒープまたは B-Tree インデックスのロック。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこの情報は不完全です。<br /><br /> AU = アロケーション ユニットのロック。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこの情報は不完全です。|  
|**リソース**|**nchar(32)**|ロックされているリソースを識別する値です。 値の形式で識別されるリソースの種類に依存、**型**列。<br /><br /> **型**値:**リソース**値<br /><br /> RID : fileid:pagenumber:rid というフォーマットの識別子です。fileid はページが含まれるファイル、pagenumber は行が含まれるページ、rid はページ上の特定の行をそれぞれ識別します。 fileid と一致する、 **file_id**内の列、 **sys.database_files**カタログ ビューです。<br /><br /> KEY : [!INCLUDE[ssDE](../../includes/ssde-md.md)]が内部的に使用する 16 進数です。<br /><br /> PAG : fileid:pagenumbe というフォーマットの番号です。fileid はページが含まれるファイル、pagenumber はページをそれぞれ識別します。<br /><br /> EXT: エクステント内の先頭ページを識別する番号です。 この番号は、fileid:pagenumber というフォーマットで指定します。<br /><br /> タブ: 情報テーブルが既にで識別されるため、提供される、 **ObjId**列です。<br /><br /> DB: 情報がありません、データベースが既にで識別されるため、 **dbid**列です。<br /><br /> FIL: に一致するファイルの識別子、 **file_id**内の列、 **sys.database_files**カタログ ビューです。<br /><br /> APP : ロックされているアプリケーション リソースの一意識別子です。 DbPrincipleId の形式で:\<リソース文字列の 16 文字に最初の 2 つ >\<ハッシュ値 >。<br /><br /> MD : リソースの種類によって異なります。 詳細については、の説明を参照して、 **resource_description**内の列[sys.dm_tran_locks &#40;です。TRANSACT-SQL と #41 です;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)。<br /><br /> HBT : 情報は提供されません。 使用して、 **sys.dm_tran_locks**動的管理ビューを代わりにします。<br /><br /> AU : 情報は提供されません。 使用して、 **sys.dm_tran_locks**動的管理ビューを代わりにします。|  
|**モード**|**nvarchar (8)**|要求されたロック モードです。 次の値をとります。<br /><br /> NULL = リソースへのアクセスが一切許可されません。 プレースホルダーとしての役割を果たします。<br /><br /> Sch-S = スキーマ安定度。 スキーマ エレメントに対してスキーマ安定度ロックが保持されているセッションの中では、テーブルやインデックスなどのスキーマ エレメントは削除されません。<br /><br /> Sch-M = スキーマ修正。 特定のリソースのスキーマを変更するセッションで保持される必要があります。 他のセッションで目的のオブジェクトが参照されないようにします。<br /><br /> S = 共有。 保持しているセッションに、リソースへの共有アクセスが許可されます。<br /><br /> U = 更新。 リソース上で取得された更新ロックが、最終的に更新されることが許可されます。 これは、複数のセッションが、後で更新する可能性があるリソースをロックするときに発生する、一般的なデッドロックの形式を防止するために使用されます。<br /><br /> X = 排他。 保持しているセッションで、リソースへの排他アクセスが許可されます。<br /><br /> IS = インテント共有。 ロック階層の下位のリソースに S ロックを設定するよう指定します。<br /><br /> IU = インテント更新。 ロック階層の下位のリソースに U ロックを設定するよう指定します。<br /><br /> IX = インテント排他。 ロック階層の下位のリソースに X ロックを設定するよう指定します。<br /><br /> SIU = 共有インテント更新。 ロック階層の下位のリソースに更新ロックを設定する目的で、リソースへの共有アクセスを指定します。<br /><br /> SIX = 共有インテント排他。 ロック階層の下位のリソースに排他ロックを設定する目的で、リソースへの共有アクセスを指定します。<br /><br /> UIX = 更新インテント排他。 ロック階層の下位のリソースに排他ロックを設定する目的で、リソースに保持する更新ロックを指定します。<br /><br /> BU = 一括更新。 一括操作で使用します。<br /><br /> RangeS_S = 共有キー範囲と共有リソース ロック。 直列化可能な範囲スキャンを指定します。<br /><br /> RangeS_U = 共有キー範囲と更新リソース ロック。 直列化可能な更新スキャンを指定します。<br /><br /> RangeI_N = 挿入キー範囲と NULL リソース ロック。 新しいキーをインデックスに挿入する前に、範囲をテストするために使用します。<br /><br /> RangeI_S = キー範囲変換ロック。 範囲 I_N ロックと S ロックの重複によって作成されます。<br /><br /> RangeI_U = 範囲 I_N と U ロックの重複によって作成されるキー範囲変換ロックです。<br /><br /> RangeI_X = 範囲 I_N と X ロックの重複によって作成されるキー範囲変換ロックです。<br /><br /> RangeX_S = 範囲 I_N と範囲 S_S ロックの重複によって作成されるキー範囲変換 ロックです。<br /><br /> RangeX_U = 範囲 I_N と範囲 S_U ロックの重複によって作成されるキー範囲変換ロックです。<br /><br /> RangeX_X = 排他キー範囲と排他リソース ロック。 範囲内のキーを更新する場合に使用する変換ロックです。|  
|**[状態]**|**nvarchar (5)**|ロック要求の状態。<br /><br /> CNVRT : ロックは別のモードから変換しようとしたが、競合するモードでロックを保持している別のプロセスによって変換がブロックされていることを示します。<br /><br /> GRANT : ロックが取得されたことを示します。<br /><br /> WAIT : 競合するモードでロックを保持している別のプロセスによってロックがブロックされていることを示します。|  
  
## <a name="remarks"></a>解説  
 次の処理を行うことで、読み込み操作のロックを制御できます。  
  
-   SET TRANSACTION ISOLATION LEVEL を使用してセッションのロック レベルを指定します。 構文と制限事項を参照してください。 [SET TRANSACTION ISOLATION LEVEL &#40;です。TRANSACT-SQL と #41 です;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)。  
  
-   ロック テーブル ヒントを使用して、FROM 句での個々のテーブル参照のロック レベルを指定します。 構文と制限事項を参照してください。[テーブル ヒント &#40;です。TRANSACT-SQL と #41 です;](../../t-sql/queries/hints-transact-sql-table.md)。  
  
 セッションに関連付けられていないすべての分散トランザクションは、孤立しているトランザクションです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]では、孤立しているすべての分散トランザクションに、-2 の SPID 値が割り当てられます。このため、ユーザーは、孤立している分散トランザクションを簡単に識別できます。 詳細については、「 [マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-locks"></a>A. すべてのロックを一覧表示する  
 次の例では、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスで現在保持されているすべてのロックに関する情報を表示します。  
  
```  
USE master;  
GO  
EXEC sp_lock;  
GO  
```  
  
### <a name="b-listing-a-lock-from-a-single-server-process"></a>B. 1 つのサーバー プロセスからロックを表示する  
 次の例では、プロセス ID `53` に関する情報を表示します。ロックなどの情報も含まれます。  
  
```  
USE master;  
GO  
EXEC sp_lock 53;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_tran_locks &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [DB_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/db-name-transact-sql.md)   
 [KILL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/kill-transact-sql.md)   
 [OBJECT_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-name-transact-sql.md)   
 [sp_who &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.dm_os_tasks と組み合わせます &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_os_threads &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)  
  
  
