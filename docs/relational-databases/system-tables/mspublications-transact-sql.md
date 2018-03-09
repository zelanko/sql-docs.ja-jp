---
title: "MSpublications (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpublications
- MSpublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublications system table
ms.assetid: 7a0b3457-7265-4f24-a255-7f055d908f20
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9541a06cddbfad77ab404c6780076c633989a5e8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mspublications-transact-sql"></a>MSpublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublications**テーブルには、パブリッシャーによってレプリケートされるパブリケーションごとに 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id などがあります。**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**publication_id**|**int**|パブリケーションの ID。|  
|**publication_type**|**int**|パブリケーションの種類。<br /><br /> **0** = トランザクションです。<br /><br /> **1**スナップショットを = です。<br /><br /> **2**マージを = です。|  
|**thirdparty_flag**|**bit**|パブリケーションがかどうかを示す、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **1**以外のデータ ソースを =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。|  
|**immediate_sync**|**bit**|スナップショット エージェントが実行されるたびに同期ファイルが作成されるか、または作り直されるかを示します。|  
|**allow_push**|**bit**|指定されたパブリケーションに対してプッシュ サブスクリプションを作成できるかどうかを示します。|  
|**allow_pull**|**bit**|指定されたパブリケーションに対してプル サブスクリプションを作成できるかどうかを示します。|  
|**allow_anonymous**|**bit**|指定されたパブリケーションに対して匿名サブスクリプションを作成できるかどうかを示します。|  
|**説明**|**nvarchar (255)**|パブリケーションの説明です。|  
|**vendor_name**|**nvarchar (100)**|パブリッシャーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のデータベースの場合の製造元の名前です。|  
|**保有期間**|**int**|パブリケーションの保有期間 (時間) です。|  
|**sync_method**|**int**|同期方法。<br /><br /> **0** = native (すべてのテーブルのネイティブ モードの一括コピー出力) します。<br /><br /> **1** = 文字 (すべてのテーブルのキャラクター モードの一括コピー出力が生成されます)。<br /><br /> **3** = 同時実行 (すべてのネイティブ モードの一括コピー出力テーブルは、スナップショット時に、テーブルをロックしませんが生成されます)。<br /><br /> **4** = Concurrent_c (すべてのキャラクター モードの一括コピー出力テーブルは、スナップショット時に、テーブルをロックしませんが生成されます)<br /><br /> 値**3**と**4**が利用可能なトランザクション レプリケーションおよびマージ レプリケーションでは、スナップショット レプリケーションではなくです。|  
|**allow_subscription_copy**|**bit**|このパブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能を有効または無効にします。 **0**コピーが無効である、ことを意味し、 **1**有効になっていることを意味します。|  
|**thirdparty_options**|**int**|指定するかどうか、パブリケーションのレプリケーション フォルダー内の表示[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]は抑制されます。<br /><br /> **0** = レプリケーション フォルダーに異種パブリケーションを表示[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。<br /><br /> **1** = 表示しないレプリケーション フォルダー内に異種パブリケーション[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。|  
|**allow_queued_tran**|**bit**|パブリケーションがキュー更新を許可するかどうかを指定します。<br /><br /> **0 =**パブリケーションはキューに置かれた非。<br /><br /> **1** = パブリケーションはキューに配置します。|  
|**オプション**|**int**|このリリースに関する情報はありません。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
