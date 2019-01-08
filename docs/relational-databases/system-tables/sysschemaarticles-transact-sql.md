---
title: sysschemaarticles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysschemaarticles_TSQL
- sysschemaarticles
dev_langs:
- TSQL
helpviewer_keywords:
- sysschemaarticles system table
ms.assetid: 67a1c039-c283-4a9c-bacc-b9b3973590c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 39444e0eaf9a44f48fc86b5d7f4595d63d1e9823
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822706"
---
# <a name="sysschemaarticles-transact-sql"></a>sysschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トランザクション パブリケーションとスナップショット パブリケーションのスキーマだけのアーティクルを追跡します。 このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクル ID です。|  
|**creation_script**|**nvarchar (255)**|ターゲット テーブルを作成するのに使用されるアーティクル スキーマのスクリプトのパスと名前です。|  
|**description**|**nvarchar (255)**|この記事の説明エントリします。|  
|**dest_object**|**sysname**|アーティクルがストアド プロシージャ、ビュー、UDF など、スキーマだけのアーティクルの場合は、サブスクリプション データベースのオブジェクト名です。|  
|**name**|**sysname**|パブリケーション内のスキーマだけのアーティクルの名前です。|  
|**objid**|**int**|アーティクル ベース オブジェクトのオブジェクト識別子。 プロシージャ、ビュー、インデックス付きビュー、または UDF のオブジェクト識別子です。|  
|**pubid**|**int**|パブリケーションの ID。|  
|**pre_creation_cmd**|**tinyint**|アーティクルのスナップショットを適用する際、サブスクライバーで同じ名前の既存のオブジェクトを検出した場合に、システムが実行する操作を指定します。<br /><br /> **0** = nothing。<br /><br /> **1** = レプリケーション先テーブルを削除します。<br /><br /> **2**ドロップ先のテーブルを = です。<br /><br /> **3** = 先テーブルを切り捨てます。|  
|**status**|**int**|アーティクルのステータスを指定するために使用するビットマップです。|  
|**type**|**tinyint**|スキーマだけのアーティクルの種類を示す値です。<br /><br /> **32**ストアド プロシージャを = です。<br /><br /> **64** = ビューまたはインデックス付きビュー。 <br /><br /> **96** = 集計関数。<br /><br /> **128**関数を = です。|  
|**schema_option**|**binary(8)**|指定されたアーティクルに対するスキーマ生成オプションのビットマスクです。 すべての CALL/MCALL/XCALL 構文の目的のデータベース内での、ストアド プロシージャの自動作成を指定します。次の値 (1 つまたは複数) のビットごとの論理和となります。<br /><br /> **0x00** = 無効にします。 使用してスナップショット エージェントによるスクリプト作成*creation_script*します。<br /><br /> **0x01** = オブジェクトの作成 (CREATE TABLE、CREATE PROCEDURE など) を生成します。 ストアド プロシージャ アーティクルの既定値です。<br /><br /> **0x02** = 定義されている場合は、アーティクルのカスタム ストアド プロシージャを生成します。<br /><br /> **0x10** = 対応するクラスター化インデックスを生成します。<br /><br /> **0x20** = ユーザー定義データ型を基本データ型に変換します。<br /><br /> **0x40**= 対応する非クラスター化インデックスを生成します。<br /><br /> **0x80**= 主キーに関する宣言参照整合性が含まれます。<br /><br /> **0x73** = CREATE TABLE ステートメントの生成、および非クラスター化インデックスが作成されますを基本データ型、ユーザー定義データ型に変換およびサブスクライバーで適用されるカスタム ストアド プロシージャのスクリプトを生成します。 ストアド プロシージャ アーティクル以外のすべてのアーティクルの既定値です。<br /><br /> **0x100**= 定義されている場合は、テーブル アーティクル上でユーザー トリガーをレプリケートします。<br /><br /> **0x200**= 外部キー制約をレプリケートします。 参照先のテーブルがパブリケーションの一部は、パブリッシュされたテーブルですべての外部キー制約はレプリケートされません。<br /><br /> **0x400**= check 制約をレプリケートします。<br /><br /> **0x800**= 既定値をレプリケートします。<br /><br /> **0x1000**= 列レベルの照合順序をレプリケートします。<br /><br /> **0x2000**= パブリッシュされたアーティクルのソース オブジェクトに関連付けられた拡張プロパティをレプリケートします。<br /><br /> **0x4000**= テーブル アーティクルで定義されている場合、一意のキーをレプリケートします。<br /><br /> **0x8000**ALTER TABLE ステートメントを使用して、制約としてレプリケートの主キーと一意キーのテーブル アーティクルを = です。|  
|**dest_owner**|**sysname**|目的のデータベースにおけるテーブルの所有者です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
