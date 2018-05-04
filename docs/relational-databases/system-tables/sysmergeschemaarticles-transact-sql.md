---
title: sysmergeschemaarticles (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergeschemaarticles_TSQL
- sysmergeschemaarticles
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergeschemaarticles system table
ms.assetid: b5085979-2f76-48e1-bf3b-765a84003dd9
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6901f0676f6c7dbbd3770389d212026b166e7de3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergeschemaarticles-transact-sql"></a>sysmergeschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ レプリケーションに関してスキーマだけのアーティクルを追跡します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|マージ パブリケーション内のスキーマだけのアーティクルの名前。|  
|**type**|**tinyint**|スキーマだけのアーティクルの種類。次のいずれかになります。<br /><br /> **0x20**ストアド プロシージャのスキーマだけのアーティクルを = です。<br /><br /> **0x40** = ビュー スキーマのみのアーティクルまたはインデックス付きビュー スキーマのみのアーティクルです。|  
|**objid**|**int**|アーティクル ベース オブジェクトのオブジェクト識別子。 プロシージャ、ビュー、インデックス付きビュー、またはユーザー定義関数のオブジェクト識別子です。|  
|**artid**|**uniqueidentifier**|アーティクル ID です。|  
|**説明**|**nvarchar (255)**|アーティクルの説明です。|  
|**pre_creation_command**|**tinyint**|サブスクリプション データベースの中でアーティクルが作成されるときに実行される既定の操作。<br /><br /> **0 =** なし - サブスクライバーでテーブルが既に存在する場合のアクションが行わします。<br /><br /> **1** = drop - テーブルを再作成する前に削除します。<br /><br /> **2** = 削除-サブセット フィルターの WHERE 句に基づいて削除します。<br /><br /> **3** = 切り捨て-として同じ**2**は行ではなくページを削除します。 ただし、WHERE 句は使用しません。|  
|**pubid**|**uniqueidentifier**|パブリケーションの一意識別子。|  
|**ステータス**|**tinyint**|スキーマだけのアーティクルの状態。次のいずれかになります。<br /><br /> **1** = Unsynced - テーブルの実行に、次回、スナップショット エージェントを実行をパブリッシュする初期処理スクリプト。<br /><br /> **2** = active - テーブルをパブリッシュする初期処理スクリプトが実行されています。<br /><br /> **5** = New_inactive - 追加します。<br /><br /> **6** = New_active - 追加します。|  
|**creation_script**|**nvarchar (255)**|ターゲット テーブルの作成に使用されるアーティクル スキーマの事前作成スクリプトのパスと名前 (省略可能)。|  
|**schema_option**|**binary(8)**|スキーマだけのアーティクルに関連するスキーマ生成オプションのビットマップ。次の値のうち 1 つ以上の結果を、ビットごとに論理和演算したものになります。<br /><br /> **0x00** = スナップショット エージェントによるスクリプト作成無効にして、提供されている CreationScript を使用します。<br /><br /> **0x01** = オブジェクトの作成 (CREATE TABLE、CREATE PROCEDURE など) を生成します。<br /><br /> **0x10** = 対応するクラスター化インデックスを生成します。<br /><br /> **0x20** convert ユーザー定義データ型を基本データ型を = です。<br /><br /> **0x40** = 生成の対応する非クラスター化インデックスまたはインデックスです。<br /><br /> **0x80** Include 主キーに関する宣言参照整合性を = です。<br /><br /> **0x100**定義されている場合、テーブル アーティクル上のレプリケート ユーザー トリガーを = です。<br /><br /> **0x200** = 外部キー制約をレプリケートします。 参照するテーブルがパブリケーションの一部でない場合は、パブリッシュされたテーブルのすべての外部キー制約がレプリケートされるわけではありません。<br /><br /> **0x400** = check 制約をレプリケートします。<br /><br /> **0x800** = 既定値をレプリケートします。<br /><br /> **0x1000** = 列レベルの照合順序をレプリケートします。<br /><br /> **0x2000** = パブリッシュされたアーティクルのソース オブジェクトに関連付けられた拡張プロパティをレプリケートします。<br /><br /> **0x4000** = テーブル アーティクルで定義されている場合、一意キーをレプリケートします。<br /><br /> **0x8000** = ALTER TABLE ステートメントを使用して、制約として主キーと一意キー、テーブルのアーティクルをレプリケートします。<br /><br /> 詳細に指定できる値について**schema_option**を参照してください[sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)です。|  
|**destination_object**|**sysname**|サブスクリプション データベース内にあるレプリケーション先オブジェクトの名前。 この値は、ストアド プロシージャ、ビュー、UDF などのスキーマだけのアーティクルにのみ適用されます。|  
|**destination_owner**|**sysname**|ない場合は、サブスクリプション データベース内のオブジェクトの所有者**dbo**です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
