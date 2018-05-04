---
title: sysextendedarticlesview (TRANSACT-SQL) |Microsoft ドキュメント
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
- sysextendedarticlesview_TSQL
- sysextendedarticlesview
dev_langs:
- TSQL
helpviewer_keywords:
- sysextendedarticlesview view
ms.assetid: 8bdd22f7-c268-49b6-820c-3fe603feb128
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 858cabc0cef5c002fede5af6e7905cd2b5cbf0e2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysextendedarticlesview-transact-sql"></a>sysextendedarticlesview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysextendedarticlesview**ビューは、パブリッシュされたアーティクルに関する情報を提供します。 このビューは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの一意な ID 番号を示す ID 列です。|  
|**creation_script**|**nvarchar (255)**|そのアーティクルのスキーマ作成スクリプトです。|  
|**del_cmd**|**nvarchar (255)**|DELETE 時に実行するコマンド、またはログから作成するコマンドです。|  
|**説明**|**nvarchar (255)**|アーティクルの説明エントリします。|  
|**dest_table**|**nvarchar(128)**|対象テーブルの名前です。|  
|**フィルター (filter)**|**int**|行方向のパーティション分割に使用するストアド プロシージャのオブジェクト識別子です。|  
|**filter_clause**|**ntext**|フィルターによる行選択に使用する、アーティクルの WHERE 句です。|  
|**ins_cmd**|**nvarchar (255)**|INSERT 時に実行するコマンドです。|  
|**name**|**nvarchar(128)**|パブリケーションの中で一意なアーティクルに関係する名前です。|  
|**objid**|**int**|パブリッシュするテーブル オブジェクト ID です。|  
|**pubid**|**int**|そのアーティクルが属するパブリケーションの ID です。|  
|**pre_creation_cmd**|**tinyint**|DROP TABLE、DELETE TABLE、または TRUNCATE 事前作成コマンドです。<br /><br /> **0** = none です。<br /><br /> **1**ドロップを = です。<br /><br /> **2** = 削除します。<br /><br /> **3** = TRUNCATE です。|  
|**ステータス**|**int**|アーティクル オプションとステータスのビットマスクです。次に示す 1 つ以上の値のビットごとの論理和演算をとります。<br /><br /> **1** = アーティクルはアクティブです。<br /><br /> **8** = INSERT ステートメントに列名を含みます。<br /><br /> **16** = ステートメント パラメーターを使用します。<br /><br /> **24** = 両方の INSERT ステートメントに列名を含めるし、パラメーター化されたステートメントを使用します。<br /><br /> たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクルの場合、この列の値は 17 になります。 値 0 は、アーティクルが非アクティブであり、追加のプロパティが定義されていないことを表します。|  
|**sync_objid**|**int**|アーティクルの定義を表すテーブルまたはビューの ID です。|  
|**type**|**tinyint**|アーティクルのタイプです。<br /><br /> **1**ログベースのアーティクルを = です。<br /><br /> **3** = 手動フィルター付きログベースのアーティクルです。<br /><br /> **5** = 手動ビュー付きログベースのアーティクルです。<br /><br /> **7** = 手動フィルターおよび手動ビュー付きログベースのアーティクルです。|  
|**upd_cmd**|**nvarchar (255)**|UPDATE 時に実行するコマンド、またはログから作成するコマンドです。|  
|**schema_option**|**[バイナリ]**|パブリッシュされたオブジェクトのどのプロパティをスナップショットにスクリプト作成するのかを示します。 サポートされるスキーマ オプションの一覧は、次を参照してください。 [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)です。|  
|**dest_owner**|**nvarchar(128)**|目的のデータベースにおけるテーブルの所有者です。|  
|**ins_scripting_proc**|**int**|INSERT ステートメントがレプリケートされるときに実行されるカスタム ストアド プロシージャまたはスクリプトのオブジェクト識別子です。|  
|**del_scripting_proc**|**int**|DELETE ステートメントがレプリケートされるときに実行されるカスタム ストアド プロシージャまたはスクリプトのオブジェクト識別子です。|  
|**upd_scripting_proc**|**int**|UPDATE ステートメントがレプリケートされるときに実行されるカスタム ストアド プロシージャまたはスクリプトのオブジェクト識別子です。|  
|**custom_script**|**int**|DDL トリガーの完了時に実行されるカスタム スクリプトまたはプロシージャのオブジェクト識別子です。|  
|**fire_triggers_on_snapshot**|**int**|スナップショットが適用されるときにレプリケートされたトリガーが実行されるかどうかを示します。次のいずれかの値をとります。<br /><br /> **0** = トリガーは実行されません。<br /><br /> **1** = トリガーは実行されます。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
