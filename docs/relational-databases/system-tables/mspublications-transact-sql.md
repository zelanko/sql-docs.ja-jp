---
title: MSpublications (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpublications
- MSpublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublications system table
ms.assetid: 7a0b3457-7265-4f24-a255-7f055d908f20
author: stevestein
ms.author: sstein
ms.openlocfilehash: de4970e82155454b3d05d6200bc7413baca97aef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939010"
---
# <a name="mspublications-transact-sql"></a>MSpublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublications**テーブルには、パブリッシャーによってレプリケートされるパブリケーションごとに1行のレコードが格納されます。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャーデータベースの名前。|  
|**レプリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**publication_id**|**int**|パブリケーションの ID です。|  
|**publication_type**|**int**|パブリケーションの種類です。<br /><br /> **0** = トランザクション。<br /><br /> **1** = スナップショット。<br /><br /> **2** = Merge。|  
|**thirdparty_flag**|**bit**|パブリケーションがデータベースで[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あるかどうかを示します。<br /><br /> **** = 0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。<br /><br /> **1** = 以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータソース。|  
|**independent_agent**|**bit**|このパブリケーションに対してスタンドアロンのディストリビューションエージェントがあるかどうかを示します。|  
|**immediate_sync**|**bit**|スナップショットエージェントが実行されるたびに同期ファイルが作成または再作成されるかどうかを示します。|  
|**allow_push**|**bit**|指定されたパブリケーションに対してプッシュサブスクリプションを作成できるかどうかを示します。|  
|**allow_pull**|**bit**|指定されたパブリケーションに対してプルサブスクリプションを作成できるかどうかを示します。|  
|**allow_anonymous**|**bit**|指定されたパブリケーションに対して匿名サブスクリプションを作成できるかどうかを示します。|  
|**記述**|**nvarchar(255)**|パブリケーションの説明です。|  
|**vendor_name**|**nvarchar (100)**|パブリッシャーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のデータベースの場合の製造元の名前です。|  
|**保有**|**int**|パブリケーションの保有期間 (時間) です。|  
|**sync_method**|**int**|同期方法:<br /><br /> **0** = native (すべてのテーブルのネイティブモードの一括コピー出力を生成します)。<br /><br /> **1** = 文字 (すべてのテーブルのキャラクターモードの一括コピー出力を生成します)。<br /><br /> **3** = 同時実行 (すべてのテーブルのネイティブモードの一括コピー出力を作成しますが、スナップショット時にテーブルをロックしません)。<br /><br /> **4** = Concurrent_c (すべてのテーブルのキャラクターモードの一括コピー出力を生成しますが、スナップショット時にテーブルをロックしません)<br /><br /> 値**3**および**4**は、トランザクションレプリケーションとマージレプリケーションで使用できますが、スナップショットレプリケーションでは使用できません。|  
|**allow_subscription_copy**|**bit**|このパブリケーションをサブスクライブするサブスクリプションデータベースをコピーする機能を有効または無効にします。 **0**は、コピーが無効であることを示します。 **1**は、コピーが有効になっていることを示します。|  
|**thirdparty_options**|**int**|の[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]レプリケーションフォルダー内のパブリケーションの表示を抑制するかどうかを指定します。<br /><br /> **0** = の[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]レプリケーションフォルダーに異種パブリケーションを表示します。<br /><br /> **1** = のレプリケーションフォルダーに異種パブリケーションを表示しないよう[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]にします。|  
|**allow_queued_tran**|**bit**|パブリケーションがキュー更新を許可するかどうかを指定します。<br /><br /> **0 =** パブリケーションはキューに登録されていません。<br /><br /> **1** = パブリケーションはキューに登録されています。|  
|**オプション**|**int**|このリリースに関する情報はありません。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
