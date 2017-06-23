---
title: "トランザクション ログ ファイルのサイズの管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-transaction-log
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 6d75e0e40c5642993cb17b09e421fbfebf40f87a
ms.openlocfilehash: cd1931ef0f77c0a1e31c29833f38c51416e267c8
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="manage-the-size-of-the-transaction-log-file"></a>トランザクション ログ ファイルのサイズの管理
このトピックの内容を監視する方法[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクション ログのサイズ、トランザクション ログの圧縮への追加またはトランザクション ログ ファイルを大きく、最適化、 **tempdb**トランザクション ログ増加率およびトランザクション ログ ファイルの容量増加を制御します。  

  ##  <a name="MonitorSpaceUse"></a> ログ領域の使用量の監視  
使用してログ領域の使用を監視[DBCC SQLPERF (LOGSPACE)](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)です。 このコマンドは、現在使用されているログ領域の量に関する情報を返し、いつトランザクション ログを切り捨てる必要があるかを示します。 詳細については、次を参照してください。 [DBCC SQLPERF TRANSACT-SQL](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)です。 現在のログ ファイルのサイズ、最大サイズ、およびファイルの自動拡張オプションについては、使用することも、**サイズ**、 **max_size**、および**成長**でそのログ ファイルの列**sys.database_files**です。 詳細については、「[sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)」を参照してください。  
  
**重要:** ログ ディスクの過負荷を避けてください。  

  
##  <a name="ShrinkSize"></a> ログ ファイルのサイズを圧縮する  
 物理ログ ファイルの物理サイズを削減するには、ログ ファイルを圧縮する必要があります。 これは、機能は、未使用領域にはトランザクション ログ ファイルが含まれていることがわかっている場合に便利です。 ログ ファイルを圧縮するには、データベースがオンラインで、少なくとも 1 つの仮想ログ ファイルが解放されている間だけです。 場合によっては、次のログの切り捨てまでログを圧縮できないことがあります。  
  
> [!NOTE]
>  実行時間の長いトランザクションなど、長期間にわたって仮想ログ ファイルがアクティブなままになる要因があると、ログの圧縮が制限されたり、ログがまったく圧縮できないことがあります。 ログの切り捨てが遅れる要因については、「[トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)」を参照してください。  
  
 ログ ファイルを圧縮すると、論理ログのどの部分も保持しない 1 つまたは複数の仮想ログ ファイル (つまり、*非アクティブな仮想ログ ファイル*) が削除されます。 トランザクション ログ ファイルを圧縮するときに、非アクティブな仮想ログ ファイルは、ログがほぼターゲット サイズを削減するログ ファイルの末尾から削除されます。  
  
 **データベース ファイルを圧縮せずにログ ファイルを圧縮する**  
  
-   [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
  
-   [ファイルの圧縮](../../relational-databases/databases/shrink-a-file.md)  
  
 **ログ ファイルの圧縮イベントを監視する**  
  
-   [Log File Auto Shrink Event Class](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md)。  
  
 **ログ領域の監視**  
  
-   [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)  
  
-   [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) (ログ ファイルまたはファイルの **size**、**max_size**、**growth** 列を参照してください。)  
  
> [!NOTE]
>  自動的に縮小するログ ファイルを設定することができます。 ただし、自動圧縮は推奨されず、 **autoshrink** データベース プロパティは既定で FALSE に設定されています。 **autoshrink** を TRUE に設定すると、ファイル領域の 25% を超える領域が未使用の場合にのみ、自動圧縮によってファイルのサイズが縮小されます。 ファイルは、ファイル領域の 25% のみが未使用領域になるサイズ、またはファイルの元のサイズの、どちらか大きい方のサイズまで圧縮されます。 **autoshrink** プロパティの設定変更については、「[データベースのプロパティの表示または変更](../../relational-databases/databases/view-or-change-the-properties-of-a-database.md)」を参照してください。**[オプション]** ページの **Auto Shrink** プロパティを使用します。あるいは、[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) の AUTO_SHRINK オプションを使用します。  
  

##  <a name="AddOrEnlarge"></a> ログ ファイルの追加または拡大  
 (ディスク領域で許可される) 場合は、既存のログ ファイルを拡大することにより、または通常は、別のディスク上のデータベースにログ ファイルを追加することによって、領域を確保することができます。  
  
-   データベースにログ ファイルを追加するには、ALTER DATABASE ステートメントの ADD LOG FILE 句を使用します。 ログ ファイルを追加すると、ログを大きくすることができます。  
  
-   ログ ファイルを拡大するには、ALTER DATABASE ステートメントの MODIFY FILE 句を使用し、SIZE および MAXSIZE 構文を指定します。 詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。  
    
  
##  <a name="tempdbOptimize"></a> tempdb トランザクション ログのサイズの最適化  
 サーバー インスタンスを再起動すると、 **tempdb** データベースのトランザクション ログのサイズが、元の自動拡張前のサイズに変更されます。 これにより、 **tempdb** のトランザクション ログのパフォーマンスが低下することがあります。 このオーバーヘッドは、サーバー インスタンスを起動または再起動した後、 **tempdb** のトランザクション ログのサイズを増やすことで回避できます。 詳細については、「 [tempdb Database](../../relational-databases/databases/tempdb-database.md)」をご覧ください。  
  
  
##  <a name="ControlGrowth"></a> トランザクション ログ ファイルのサイズ拡大の管理  
 使用して、 [ALTER DATABASE (TRANSACT-SQL)](../../t-sql/statements/alter-database-transact-sql.md)トランザクション ログ ファイルの増加に対応するステートメント。 次のことを考慮してください。  
  
-   現在のサイズを KB、MB、GB、および TB 単位で変更する場合は、SIZE オプションを使用します。  
  -   拡張増分値で変更するには、FILEGROWTH オプションを使用します。 0 は、自動拡張がオフで、領域を追加できないことを示します。 ログ ファイルの自動拡張の増分値が小さい場合も、パフォーマンスが低下することがあります。 ログ ファイルの拡張増分値は、拡張を頻繁に行わなくても済むように十分な大きさにする必要があります。 通常は、既定の拡張増分値 (10%) が適しています。  

ログ ファイルのファイル拡張プロパティを変更する方法については、「 [ALTER DATABASE (Transact-SQL)](https://msdn.microsoft.com/library/ms174269.aspx)」を参照してください。  
  
-   ログ ファイルの最大サイズを KB、MB、GB、および TB 単位で制御するか、拡張値を UNLIMITED に設定するには、MAXSIZE オプションを使用します。  
  
  
## <a name="see-also"></a>参照  
 [BACKUP (TRANSACT-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [完全なトランザクション ログ (SQL Server エラー 9002) のトラブルシューティングします。](../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  

