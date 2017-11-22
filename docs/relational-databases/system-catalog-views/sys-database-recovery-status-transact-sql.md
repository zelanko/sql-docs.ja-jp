---
title: "sys.database_recovery_status (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/12/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- database_recovery_status_TSQL
- database_recovery_status
- sys.database_recovery_status
- sys.database_recovery_status_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.database_recovery_status catalog view
ms.assetid: 46fab234-1542-49be-8edf-aa101e728acf
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc080e2f9a7dd102dcd9fa760ffc6267430fb30f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaserecoverystatus-transact-sql"></a>sys.database_recovery_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースごとに 1 行のデータを格納します。 データベースが起動していない場合は、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によってデータベースの起動が試行されます。  
  
 以外のデータベースの行を表示する**マスター**または**tempdb**次のいずれかが当てはまる必要があります。  
  
-   データベースの所有者であること。  
  
-   ALTER ANY DATABASE または VIEW ANY DATABASE のサーバー レベルの権限が与えられていること。  
  
-   CREATE DATABASE 権限がある、**マスター**データベース。    
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意のデータベースの ID です。|  
|**database_guid**|**uniqueidentifier**|データベースのすべてのデータベース ファイルを相互に関連付ける場合に使用します。 データベースが適切に起動するには、すべてのファイルのヘッダー ページにこの GUID が定義されている必要があります。 この GUID が存在するのは 1 つのデータベースのみですが、データベースをコピーしたりアタッチすると重複したデータベースが作成される場合があります。 RESTORE を実行すると、まだ存在しないデータベースの復元時に常に新しい GUID が生成されます。<br /><br /> NULL= データベースがオフラインであるか起動しない。|  
|**family_guid**|**uniqueidentifier**|一致する復元状態を検出するための、データベースの "バックアップ ファミリ" の識別子。<br /><br /> NULL = データベースがオフラインか、データベースは開始されません。|  
|**last_log_backup_lsn**|**numeric(25,0)**|次のログ バックアップの開始ログ シーケンス番号。<br /><br /> NULL の場合、トランザクション ログ バックアップを実行できません、データベースが単純復旧するか、現在のデータベース バックアップがないためです。|  
|**recovery_fork_guid**|**uniqueidentifier**|データベースがアクティブになっている、現在の復旧分岐の識別子。<br /><br /> NULL= データベースがオフラインであるか起動しない。|  
|**first_recovery_fork_guid**|**uniqueidentifier**|最初の復旧分岐の識別子。<br /><br /> NULL= データベースがオフラインであるか起動しない。|  
|**fork_point_lsn**|**numeric(25,0)**|場合**first_recovery_fork_guid**が等しくない (! =) を**recovery_fork_guid**、 **fork_point_lsn**現在の分岐ポイントのログ シーケンス番号です。 それ以外の場合は NULL になります。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
