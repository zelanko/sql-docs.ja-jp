---
title: データを復元しないデータベースの復旧 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], recovery-only
- recovery-only scenario [SQL Server]
- restoring databases [SQL Server], recovery-only
- recovery [SQL Server], recovery-only
- database recovery [SQL Server]
- database restores [SQL Server], recovery-only
- recovery [SQL Server], without restoring data
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2109346c60ca807dcc818941f9baff862a211247
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62921816"
---
# <a name="recover-a-database-without-restoring-data-transact-sql"></a>データを復元しないデータベースの復旧 (Transact-SQL)
  通常、データベースを復旧する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのすべてのデータを復元します。 ただし、実際にバックアップを復元しなくても、復元操作でデータベースを復旧することは可能です。たとえば、データベースと一貫性のある読み取り専用ファイルを復旧する場合などです。 これは、 *復旧のみの復元*と呼ばれます。 オフライン データが既にデータベースと一貫性があり、データを使用可能にするだけでよい場合、復旧のみの復元を実行することで、データベースの復旧が完了し、データがオンラインになります。  
  
 復旧のみの復元は、データベース全体、1 つまたは複数のファイル、およびファイル グループに対して行うことができます。  
  
## <a name="recovery-only-database-restore"></a>復旧のみのデータベース復元  
 復旧のみのデータベース復元は、次の場合に役に立ちます。  
  
-   復元シーケンスで前回のバックアップを復元したときはデータベースを復旧しなかったが、現在そのデータベースを復旧してオンラインにする必要がある場合。  
  
-   データベースがスタンバイ モードであり、別のログ バックアップを適用せずにそのデータベースを更新可能にする場合。  
  
 復旧のみのデータベース復元の [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 構文は次のとおりです。  
  
 RESTORE DATABASE *database_name* WITH RECOVERY  
  
> [!NOTE]  
>  バックアップは**=** \<必要ないため、from *backup_device>* 句は復旧のみの復元には使用されません。  
  
 **例**  
  
 次の例では、データを復元しない復元操作で [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを復旧します。  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## <a name="recovery-only-file-restore"></a>復旧のみのファイル復元  
 復旧のみのファイル復元は、次の場合に役に立ちます。  
  
 データベースを段階的に部分復元する場合。 プライマリ ファイル グループの復元が完了した後、復元されていないのに、新しいデータベースの状態と一貫性があるファイルが 1 つ以上ある場合。これはおそらく、しばらくの間読み取り専用であったことが原因です。 このようなファイルに対して必要な作業は、復旧のみです。データをコピーする必要はありません。  
  
 復旧のみの復元操作では、オフラインのファイル グループ内のデータをオンラインにします。データのコピー フェーズ、再実行フェーズ、および元に戻すフェーズはありません。 復元の各フェーズに関する詳細については、「[復元と復旧の概要 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)」を参照してください。  
  
 復旧のみのファイル復元の [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 構文は次のとおりです。  
  
 RESTORE DATABASE *database_name* {FILE **=** _logical_file_name_ |ファイル**=** グループ_logical_filegroup_name_ } [ **,**...*n* ] 回復  
  
 **例**  
  
 次の例は、 `SalesGroup2`データベースのセカンダリ ファイル グループ `Sales` に含まれているファイルの復旧のみのファイル復元を示しています。 プライマリ ファイル グループは段階的な部分復元の最初の手順で既に復元されており、 `SalesGroup2` は復元されたプライマリ ファイル グループと一貫性があります。 このファイル グループを復旧してオンラインにするために必要なのは、次に示す 1 つのステートメントだけです。  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## <a name="examples-of-completing-a-piecemeal-restore-scenario-with-a-recovery-only-restore"></a>復旧のみの復元を使用した段階的な部分復元シナリオの完了の例  
 **単純復旧モデル**  
  
-   [例: データベース &#40;単純復旧モデルの段階的な部分復元&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [例: 一部のファイルグループのみを &#40;単純復旧モデルの段階的な部分復元&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 **完全復旧モデル**  
  
-   [例: データベース &#40;完全復旧モデルの段階的な部分復元&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [例: 完全復旧モデル &#40;一部のファイルグループのみを復元する段階的な部分復元&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## <a name="see-also"></a>参照  
 [オンライン復元 &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)   
 [ファイル復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md)   
 [完全復旧モデルのファイル復元 &#40;&#41;](file-restores-full-recovery-model.md)   
 [Transact-sql&#41;の復元 &#40;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
