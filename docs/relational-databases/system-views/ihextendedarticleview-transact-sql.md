---
title: IHextendedArticleView (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- IHextendedArticleView_TSQL
- IHextendedArticleView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedArticleView view
ms.assetid: 19ef0a12-3214-4bb0-9c25-a665897e65a2
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d0d85b15075177fe103dab27ca0c09745b62bae
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ihextendedarticleview-transact-sql"></a>IHextendedArticleView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHextendedArticleView**ビューは、SQL Server 以外のパブリケーションでアーティクルに関する情報を公開します。 このビューは、**配布**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|パブリッシャーの一意識別子です。|  
|**publication_id**|**int**|パブリケーションの一意識別子です。|  
|**article**|**sysname**|アーティクルの名前|  
|**destination_object**|**sysname**|サブスクライバー側でパブリッシュされたオブジェクトの名前です。|  
|**source_owner**|**sysname**|パブリッシャー側でパブリッシュされたオブジェクトの所有者です。|  
|**source_object**|**sysname**|パブリッシュ側でパブリッシュされたオブジェクトの名前です。|  
|**説明**|**nvarchar (255)**|アーティクルの説明です。|  
|**creation_script**|**nvarchar (255)**|そのアーティクルのスキーマ作成スクリプトです。|  
|**del_cmd**|**nvarchar (255)**|DELETE に対して実行されるコマンドです。|  
|**フィルター (filter)**|**int**|行方向のパーティション分割を定義するために使用するストアド プロシージャの識別子です。|  
|**filter_clause**|**ntext**|アーティクルを行方向にフィルター選択するために使用する WHERE 句です。|  
|**ins_cmd**|**nvarchar (255)**|INSERT に対して実行されるコマンドです。|  
|**pre_creation_cmd**|**tinyint**|DROP TABLE、DELETE TABLE、または TRUNCATE 事前作成コマンド:<br /><br /> **0** = none です。<br /><br /> **1**ドロップを = です。<br /><br /> **2** = 削除します。<br /><br /> **3** = TRUNCATE です。|  
|**ステータス**|**tinyint**|アーティクル オプションとステータスのビットマスクです。次に示す 1 つ以上の値のビットごとの論理和演算をとります。<br /><br /> **1** = アーティクルはアクティブです。<br /><br /> **8** = INSERT ステートメントに列名を含みます。<br /><br /> **16** = ステートメント パラメーターを使用します。<br /><br /> **24** = 両方の INSERT ステートメントに列名を含めるし、パラメーター化されたステートメントを使用します。<br /><br /> たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクル、値はの**17**この列にします。 値**0**アーティクルがアクティブでないと、追加のプロパティが定義されていないことを意味します。|  
|**type**|**tinyint**|アーティクルの種類。<br /><br /> **1**ログベースのアーティクルを = です。<br /><br /> **3** = 手動フィルター付きログベースのアーティクルです。<br /><br /> **5** = 手動ビュー付きログベースのアーティクルです。<br /><br /> **7** = 手動フィルターおよび手動ビュー付きログベースのアーティクルです。|  
|**upd_cmd**|**nvarchar (255)**|UPDATE に対して実行されるコマンドです。|  
|**schema_option**|**[バイナリ]**|スクリプト作成の対象です。参照してください[sp_addarticle &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)サポートされるスキーマ オプションの一覧についてはします。|  
|**dest_owner**|**sysname**|目的のデータベースでパブリッシュされたオブジェクトの所有者です。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
