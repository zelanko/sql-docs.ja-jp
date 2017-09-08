---
title: "DBCC (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC
- DBCC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactional consistency
- Database Console Command statements
- status information [SQL Server], DBCC statements
- snapshots [SQL Server database snapshots], DBCC statements
- emergency database state [SQL Server]
- TABLOCK
- internal database snapshots [SQL Server]
- reporting DBCC statement progress
- logical consistency of data [SQL Server]
- DBCC statements
- validation statements [SQL Server]
- miscellaneous statements [SQL Server]
- statements [SQL Server], DBCC statements
- DBCC commands [SQL Server]
- result sets [SQL Server], DBCC statements
- maintenance statements [SQL Server]
- physical consistency of data [SQL Server]
- current DBCC statement status
- progress reporting [DBCC statements]
- informational statements [SQL Server]
ms.assetid: c6da8c04-5b6b-459a-9f76-110c92ca8b29
caps.latest.revision: 50
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8e8750f4b44ec206bb5a26586acd6b567f7dac37
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-transact-sql"></a>DBCC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[tsql](../../includes/tsql-md.md)] プログラミング言語には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベース コンソール コマンドとして機能する DBCC ステートメントが用意されています。
  
データベース コンソール コマンドは、次のように分類されます。
  
|コマンドの分類|実行内容|  
|---|---|
|メンテナンス|データベース、インデックスまたはファイル グループを対象とするメンテナンス タスク。|  
|その他|トレース フラグの有効化やメモリからの DLL の削除など、その他のタスク。|  
|情報|さまざまな種類の情報を収集および表示するタスク。|  
|検証|データベース、テーブル、インデックス、カタログ、ファイル グループ、またはデータベース ページの割り当ての検証操作。|  
  
DBCC コマンドは入力パラメーターをとり、値を返します。 すべての DBCC コマンド パラメーターには、Unicode と DBCS の両方のリテラルを使用できます。
  
## <a name="dbcc-internal-database-snapshot-usage"></a>DBCC 内部データベース スナップショットの使用  
次の DBCC コマンドは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で作成される内部の読み取り専用データベース スナップショットに対して実行でき、 これにより、コマンド実行時のブロックや同時実行の問題を回避できます。 詳細については、「[データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)」を参照してください。
- DBCC CHECKALLOC
- DBCC CHECKCATALOG
- DBCC CHECKDB
- DBCC CHECKFILEGROUP
- DBCC CHECKTABLE

これらの DBCC コマンドのいずれかを実行するときに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]データベース スナップショットを作成し、これをトランザクション全体で一貫性のある状態にします。 その後、DBCC コマンドではこのスナップショットに対するチェックが行われます。 DBCC コマンドの完了後、このスナップショットは削除されます。
  
内部データベース スナップショットが必要ではない場合や、内部データベース スナップショットを作成できない場合、 DBCC コマンドは実際のデータベースに対して実行されます。 データベースがオンラインの場合、DBCC コマンドではテーブルロックを使用して、チェックするオブジェクトの一貫性を確保します。 この動作は、WITH TABLOCK オプションが指定される場合と同じです。
  
次の条件で DBCC コマンドを実行する場合、内部データベース スナップショットは作成されません。
-   に対して**マスター**のインスタンスと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がシングル ユーザー モードで実行します。  
-   以外のデータベースに対して**マスター**、ALTER DATABASE ステートメントを使用してのシングル ユーザー モードでデータベースに格納されたが、します。  
-   読み取り専用データベースに対して実行する場合。  
-   ALTER DATABASE ステートメントによって緊急モードに設定されたデータベースに対して実行する場合。  
-   に対して**tempdb**です。 この場合、内部的な制約のため、データベース スナップショットは作成できません。  
-   WITH TABLOCK オプションを使用する場合。 この場合、DBCC ではデータベース スナップショットは作成されず、要求が受け入れられます。  
  
DBCC コマンドを次の対象に実行する場合は、内部データベース スナップショットの代わりにテーブル ロックが使用されます。
-   読み取り専用のファイル グループ  
-   FAT ファイル システム  
-   "名前付きストリーム" がサポートされないボリューム  
-   "代替ストリーム" がサポートされないボリューム  
  
> [!NOTE]  
>  WITH TABLOCK オプションを使用して、DBCC CHECKALLOC を実行する場合、または DBCC CHECKDB の同様な機能を実行する場合は、データベースの排他 (X) ロックが必要です。 このデータベース ロックを設定できません**tempdb**または**マスター**は他のすべてのデータベースでも失敗する可能性です。  
  
> [!NOTE]  
>  に対して実行したときに、DBCC CHECKDB が失敗した**マスター**場合は、内部データベース スナップショットを作成することはできません。  
  
## <a name="progress-reporting-for-dbcc-commands"></a>DBCC コマンドの進行状況レポート  
**Sys.dm_exec_requests**カタログ ビューには、進行状況と、DBCC CHECKDB、CHECKFILEGROUP、および CHECKTABLE コマンドの実行の現在のフェーズに関する情報が含まれています。 **Percent_complete**列は、コマンドの完了率を示す、**コマンド**列は、コマンドの実行の現在のフェーズを報告します。
  
レポートされる進行状況のレベルは、DBCC コマンド実行の現在のフェーズによって異なります。 たとえば、フェーズによって、進行状況がデータベース ページ レベルでレポートされる場合と、データベース レベルまたはアロケーション修復レベルでレポートされる場合があります。 次の表は、実行の各フェーズと、コマンドでレポートされる進行状況のレベルです。
  
|実行フェーズ|Description|進行状況レポートの単位|  
|---------------------|-----------------|------------------------------------|  
|DBCC TABLE CHECK|このフェーズでは、データベースのオブジェクトの論理的および物理的な一貫性がチェックされます。|進行状況はデータベース ページ レベルでレポートされます。<br /><br /> オンになっている各 1,000 年データベース ページの進行状況レポートの値が更新されます。|  
|DBCC TABLE REPAIR|このフェーズでは、REPAIR_FAST、REPAIR_REBUILD、または REPAIR_ALLOW_DATA_LOSS が指定され、修復が必要なオブジェクト エラーがある場合に、データベース修復が実行されます。|進行状況は個々の修復レベルでレポートされます。<br /><br /> カウンターは修復が完了するたびに更新されます。|  
|DBCC ALLOC CHECK|このフェーズでは、データベースの割り当て構造がチェックされます。<br /><br /> 注: DBCC CHECKALLOC では、同じチェックを実行します。|進行状況が報告されていません|  
|DBCC ALLOC REPAIR|このフェーズでは、REPAIR_FAST、REPAIR_REBUILD、または REPAIR_ALLOW_DATA_LOSS が指定され、修復が必要なアロケーション エラーがある場合に、データベース修復が実行されます。|進行状況はレポートされません。|  
|DBCC SYS CHECK|このフェーズでは、データベース システム テーブルがチェックされます。|進行状況はデータベース ページ レベルでレポートされます。<br /><br /> 進行状況レポートの値は、1,000 データベース ページがチェックされるたびに更新されます。|  
|DBCC SYS REPAIR|このフェーズでは、REPAIR_FAST、REPAIR_REBUILD、または REPAIR_ALLOW_DATA_LOSS が指定され、修復が必要なシステム テーブル エラーがある場合に、データベース修復が実行されます。|進行状況は個々の修復レベルでレポートされます。<br /><br /> カウンターは修復が完了するたびに更新されます。|  
|DBCC SSB CHECK|このフェーズでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker オブジェクトがチェックされます。<br /><br /> 注: DBCC CHECKTABLE を実行すると、このフェーズは実行されません。|進行状況はレポートされません。|  
|DBCC CHECKCATALOG|このフェーズでは、データベース カタログの一貫性がチェックされます。<br /><br /> 注: DBCC CHECKTABLE を実行すると、このフェーズは実行されません。|進行状況はレポートされません。|  
|DBCC IVIEW CHECK|このフェーズでは、データベースに存在するインデックス付きビューの論理的な一貫性がチェックされます。|進行状況は、チェックされたデータベース ビュー レベルでレポートされます。|  
  
## <a name="informational-statements"></a>情報ステートメント  
  
|||  
|-|-|  
|[DBCC INPUTBUFFER](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)|[DBCC SHOWCONTIG](../../t-sql/database-console-commands/dbcc-showcontig-transact-sql.md)|  
|[DBCC OPENTRAN](../../t-sql/database-console-commands/dbcc-opentran-transact-sql.md)|[DBCC SQLPERF](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)|  
|[DBCC OUTPUTBUFFER](../../t-sql/database-console-commands/dbcc-outputbuffer-transact-sql.md)|[DBCC TRACESTATUS](../../t-sql/database-console-commands/dbcc-tracestatus-transact-sql.md)|  
|[DBCC PROCCACHE](../../t-sql/database-console-commands/dbcc-proccache-transact-sql.md)|[DBCC USEROPTIONS](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)|  
|[DBCC SHOW_STATISTICS で](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)||  
  
## <a name="validation-statements"></a>検証ステートメント  
  
|||  
|-|-|  
|[DBCC CHECKALLOC](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md)|[DBCC CHECKFILEGROUP](../../t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql.md)|  
|[DBCC CHECKCATALOG](../../t-sql/database-console-commands/dbcc-checkcatalog-transact-sql.md)|[DBCC CHECKIDENT](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)|  
|[DBCC CHECKCONSTRAINTS](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md)|[DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)|  
|[DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)||  
  
## <a name="maintenance-statements"></a>メンテナンス ステートメント  
  
|||  
|-|-|  
|[DBCC CLEANTABLE](../../t-sql/database-console-commands/dbcc-cleantable-transact-sql.md)|[DBCC INDEXDEFRAG](../../t-sql/database-console-commands/dbcc-indexdefrag-transact-sql.md)|  
|[DBCC DBREINDEX](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)|[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)|  
|[DBCC DROPCLEANBUFFERS](../../t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql.md)|[DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)|  
|[DBCC FREEPROCCACHE](../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)|[DBCC UPDATEUSAGE](../../t-sql/database-console-commands/dbcc-updateusage-transact-sql.md)|  
  
## <a name="miscellaneous-statements"></a>その他のステートメント  
  
|||  
|-|-|  
|[DBCC dllname (無料)](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)|[DBCC のヘルプ](../../t-sql/database-console-commands/dbcc-help-transact-sql.md)|  
|[DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md)|[DBCC TRACEOFF](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)|  
|[DBCC FREESESSIONCACHE](../../t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)|[DBCC TRACEON](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md)|  
|[DBCC FREESYSTEMCACHE](../../t-sql/database-console-commands/dbcc-freesystemcache-transact-sql.md)|[DBCC CLONEDATABASE](https://support.microsoft.com/en-us/kb/3177838) <br /><br /> **適用されます**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Service Pack 2 です。|  
  
  

