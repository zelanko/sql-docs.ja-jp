---
title: "チェックポイント (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKPOINT_TSQL
- CHECKPOINT
dev_langs: TSQL
helpviewer_keywords:
- events [SQL Server], checkpoints
- automatic checkpoints
- writing dirty pages to disk
- pages [SQL Server], dirty
- checkpoints [SQL Server]
- CHECKPOINT statement
- log truncate mode [SQL Server]
- dirty pages
- logs [SQL Server], checkpoints
- manual checkpoints [SQL Server]
- pages [SQL Server], checkpoints
ms.assetid: ccdfc689-ad4e-44c0-83f7-0f2cfcfb6406
caps.latest.revision: "59"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6353bd534827ff9066bd7b184a09d67b5867c3cb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="checkpoint-transact-sql"></a>CHECKPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  手動チェックポイントを生成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースは現在、接続先をします。  
  
> [!NOTE]  
>  さまざまな種類のデータベースのチェックポイントと一般的なチェックポイント操作については、次を参照してください。[データベース チェックポイント &#40;です。SQL Server &#41;](../../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CHECKPOINT [ checkpoint_duration ]  
```  
  
## <a name="arguments"></a>引数  
 *checkpoint_duration*  
 手動チェックポイントを完了するのに必要な時間を秒単位で指定します。 ときに*checkpoint_duration*を指定すると、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]要求された時間内にチェックポイントを実行しようとしています。 *Checkpoint_duration*型の式を指定する必要があります**int** 0 より大きい値にする必要があります。 このパラメーターを省略すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]データベース アプリケーションのパフォーマンスに影響を最小限に抑えるチェックポイントの持続時間を調整します。 *checkpoint_duration*高度なオプションです。  
  
## <a name="factors-affecting-the-duration-of-checkpoint-operations"></a>チェックポイントの操作時間に影響を与える要因  
 通常、書き込む必要のあるダーティ ページの数が増えると、チェックポイント操作に必要とされる時間が長くなります。 他のアプリケーションのパフォーマンスに与える影響を最小にするため、既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってチェックポイント操作による書き込み頻度が調節されます。 書き込みの頻度が減ると、チェックポイント操作の完了に必要な時間は長くなります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]手動チェックポイントの場合を除き、この戦略を使用して、 *checkpoint_duration*値は、CHECKPOINT コマンドで指定します。  
  
 使用してパフォーマンスに与える影響*checkpoint_duration*ダーティ ページで、システム、および実際の期間を指定したアクティビティの数によって異なります。 たとえば、チェックポイントは、通常、120 秒で完了を指定する、 *checkpoint_duration* 45 秒の原因の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定で割り当てられるよりも、チェックポイントに他のリソースを使用します。 これに対し、指定する、 *checkpoint_duration*を 180 秒になる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を既定で割り当てられるよりも少ないリソースを割り当てます。 一般に、短い*checkpoint_duration*長い、チェックポイントに割り当てるリソースを増やす*checkpoint_duration*チェックポイントに割り当てるリソースが減少します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、常に可能な限りチェックポイントを完了し、チェックポイントが完了するとすぐに CHECKPOINT ステートメントによって値が返されます。 したがってチェックポイントの完了は、状況に応じて、指定した時間よりも早まったり、遅くなることがあります。  
  
##  <a name="Security"></a> セキュリティ  
  
### <a name="permissions"></a>権限  
 CHECKPOINT のアクセス許可が既定のメンバーに、 **sysadmin**固定サーバー ロールおよび**db_owner**と**db_backupoperator**固定データベース ロールとは譲渡します。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [データベース チェックポイント &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Recovery interval サーバー構成オプションを構成します。](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)   
 [シャット ダウン &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/shutdown-transact-sql.md)  
  
  
