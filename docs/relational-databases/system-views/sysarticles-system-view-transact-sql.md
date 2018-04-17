---
title: sysarticles (システム ビュー) (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysarticles
- sysarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticles view
ms.assetid: 18f8c9b3-cab7-4e8f-8754-11ac38c3f789
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2165a1e6909e8c02468a89bf18a0fe9cdb280c56
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysarticles-system-view-transact-sql"></a>sysarticles (システム ビュー) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticles**ビュー アーティクルのプロパティを公開します。 このビューは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの一意な ID 番号を示す ID 列です。|  
|**creation_script**|**nvarchar (255)**|そのアーティクルのスキーマ スクリプトです。|  
|**del_cmd**|**nvarchar (255)**|DELETE 時に実行するコマンド、またはログから作成するコマンドです。|  
|**説明**|**nvarchar (255)**|アーティクルの説明エントリします。|  
|**dest_table**|**sysname**|対象テーブルの名前です。|  
|**フィルター (filter)**|**int**|行方向のパーティション分割に使用するストアド プロシージャの ID です。|  
|**filter_clause**|**ntext**|フィルターによる行選択に使用する、アーティクルの WHERE 句です。|  
|**ins_cmd**|**nvarchar (255)**|INSERT 時に実行するコマンド、またはログから作成するコマンドです。|  
|**name**|**sysname**|パブリケーションの中で一意なアーティクルに関係する名前です。|  
|**objid**|**int**|パブリッシュするテーブル オブジェクト ID です。|  
|**pubid**|**int**|そのアーティクルが属するパブリケーションの ID です。|  
|**pre_creation_cmd**|**tinyint**|DROP TABLE、DELETE TABLE、または TRUNCATE 事前作成コマンドです。<br /><br /> **0** = none です。<br /><br /> **1**ドロップを = です。<br /><br /> **2** = 削除します。<br /><br /> **3** = TRUNCATE です。|  
|**ステータス**|**tinyint**|アーティクル オプションとステータスのビットマスクです。次に示す 1 つ以上の値のビットごとの論理和演算をとります。<br /><br /> **1** = アーティクルはアクティブです。<br /><br /> **8** = INSERT ステートメントに列名を含みます。<br /><br /> **16** = ステートメント パラメーターを使用します。<br /><br /> **24** = 両方の INSERT ステートメントに列名を含めるし、パラメーター化されたステートメントを使用します。<br /><br /> **64**変換可能なサブスクリプションによってアーティクルを定義する場合は、行方向のパーティションを = です。<br /><br /> たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクル、値はの**17**この列にします。 値**0**アーティクルがアクティブでないと、追加のプロパティが定義されていないことを意味します。|  
|**sync_objid**|**int**|アーティクルの定義を表すテーブルまたはビューの ID です。|  
|**type**|**tinyint**|アーティクルのタイプです。<br /><br /> **1**ログベースのアーティクルを = です。<br /><br /> **3** = 手動フィルター付きログベースのアーティクルです。<br /><br /> **5** = 手動ビュー付きログベースのアーティクルです。<br /><br /> **7** = 手動フィルターおよび手動ビュー付きログベースのアーティクルです。<br /><br /> **8**ストアド プロシージャの実行を = です。<br /><br /> **24**シリアル化可能なストアド プロシージャの実行を = です。<br /><br /> **32** = ストアド プロシージャ (スキーマのみ)。<br /><br /> **64** = ビュー (スキーマのみ)。<br /><br /> **128** = 関数 (スキーマのみ)。|  
|**upd_cmd**|**nvarchar (255)**|UPDATE 時に実行するコマンド、またはログから作成するコマンドです。|  
|**schema_option**|**binary(8)**|アーティクルに対するスキーマ生成オプションのビットマスクです。サブスクライバーへの配信用にスクリプト化されるアーティクル スキーマの部分を制御します。 スキーマ オプションの詳細については、「[sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)」を参照してください。|  
|**dest_owner**|**sysname**|目的のデータベースにおけるテーブルの所有者です。|  
|**ins_scripting_proc**|**int**|INSERT ステートメントがレプリケートされるときに実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**del_scripting_proc**|**int**|DELETE ステートメントがレプリケートされるときに実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**upd_scripting_proc**|**int**|UPDATE ステートメントがレプリケートされるときに実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**custom_script**|**nvarchar(2048)**|DDL トリガーの最後に実行される登録済みのカスタム ストアド プロシージャまたはスクリプトです。|  
|**fire_triggers_on_snapshot**|**bit**|スナップショットが適用されるときにレプリケートされたトリガーが実行されるかどうかを示します。次のいずれかの値をとります。<br /><br /> **0** = トリガーは実行されません。<br /><br /> **1** = トリガーは実行されます。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
