---
title: "sysarticles (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- sysarticles
- sysarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticles system table
ms.assetid: 9d9d5d51-6d8f-4e42-84a9-82e58eb0301e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2ce368158e29c1ba76442e38d374a5ddd615f75f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysarticles-transact-sql"></a>sysarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ローカル データベース内で定義されているアーティクルごとに 1 行のデータを保持します。 このテーブルは、パブリッシュされたデータベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの一意な ID 番号を示す ID 列です。|  
|**creation_script**|**nvarchar (255)**|そのアーティクルのスキーマ スクリプトです。|  
|**del_cmd**|**nvarchar (255)**|テーブル アーティクルの削除をレプリケートするときに使用されるレプリケーション コマンドの種類です。 詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。|  
|**説明**|**nvarchar (255)**|アーティクルの説明エントリします。|  
|**dest_table**|**sysname**|対象テーブルの名前です。|  
|**フィルター (filter)**|**int**|行方向のパーティション分割に使用するストアド プロシージャの ID です。|  
|**filter_clause**|**ntext**|フィルターによる行選択に使用する、アーティクルの WHERE 句です。|  
|**ins_cmd**|**nvarchar (255)**|テーブル アーティクルの挿入をレプリケートするときに使用されるレプリケーション コマンドの種類です。 詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。|  
|**name**|**sysname**|パブリケーションの中で一意なアーティクルに関係する名前です。|  
|**オブジェクト id**|**int**|パブリッシュするテーブル オブジェクト ID です。|  
|**pubid**|**int**|そのアーティクルが属するパブリケーションの ID です。|  
|**pre_creation_cmd**|**tinyint**|DROP TABLE、DELETE TABLE、または TRUNCATE 事前作成コマンドです。<br /><br /> **0** = none です。<br /><br /> **1**ドロップを = です。<br /><br /> **2** = 削除します。<br /><br /> **3** = TRUNCATE です。|  
|**ステータス**|**tinyint**|アーティクル オプションとステータスのビットマスクです。次に示す 1 つ以上の値のビットごとの論理和演算をとります。<br /><br /> **1** = アーティクルはアクティブです。<br /><br /> **8** = INSERT ステートメントに列名を含みます。<br /><br /> **16** = ステートメント パラメーターを使用します。<br /><br /> **24** = 両方の INSERT ステートメントに列名を含めるし、パラメーター化されたステートメントを使用します。<br /><br /> **64** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクル、値はの**17**この列にします。 値**0**アーティクルがアクティブでないと、追加のプロパティが定義されていないことを意味します。|  
|**sync_objid**|**int**|アーティクルの定義を表すテーブルまたはビューの ID です。|  
|**型**|**tinyint**|アーティクルのタイプです。<br /><br /> **1**ログベースのアーティクルを = です。<br /><br /> **3** = 手動フィルター付きログベースのアーティクルです。<br /><br /> **5** = 手動ビュー付きログベースのアーティクルです。<br /><br /> **7** = 手動フィルターおよび手動ビュー付きログベースのアーティクルです。<br /><br /> **8**ストアド プロシージャの実行を = です。<br /><br /> **24**シリアル化可能なストアド プロシージャの実行を = です。<br /><br /> **32** = ストアド プロシージャ (スキーマのみ)。<br /><br /> **64** = ビュー (スキーマのみ)。<br /><br /> **128** = 関数 (スキーマのみ)。|  
|**upd_cmd**|**nvarchar (255)**|テーブル アーティクルの更新をレプリケートするときに使用されるレプリケーション コマンドの種類です。 詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。|  
|**schema_option**|**binary (8)**|アーティクルに対するスキーマ生成オプションのビットマスクです。サブスクライバーへの配信用にスクリプト化されるアーティクル スキーマの部分を制御します。 スキーマ オプションの詳細については、「[sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)」を参照してください。|  
|**dest_owner**|**sysname**|目的のデータベースにおけるテーブルの所有者です。|  
|**ins_scripting_proc**|**int**|INSERT ステートメントがレプリケートされるときに実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**del_scripting_proc**|**int**|DELETE ステートメントがレプリケートされるときに実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**upd_scripting_proc**|**int**|UPDATE ステートメントがレプリケートされるときに実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**custom_script**|**nvarchar (2048)**|DDL トリガーの最後に実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**fire_triggers_on_snapshot**|**bit**|トリガーが実行されるスナップショットを適用すると、これらの値のいずれかを指定することがレプリケートされるかどうかを示します。<br /><br /> **0** = トリガーは実行されません。<br /><br /> **1** = トリガーは実行されます。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)  
  
  
