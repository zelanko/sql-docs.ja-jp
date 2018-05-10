---
title: sys.dm_repl_articles (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_articles_TSQL
- dm_repl_articles
- dm_repl_articles_TSQL
- sys.dm_repl_articles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_articles dynamic management function
ms.assetid: 794d514e-bacd-432e-a8ec-3a063a97a37b
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4d1e7ccd9f4bc09bde7ac3be680356b8e93a3827
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmreplarticles-transact-sql"></a>sys.dm_repl_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション トポロジ内のアーティクルとしてパブリッシュされたデータベース オブジェクトに関する情報を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artcache_db_address**|**varbinary(8)**|パブリケーション データベースに関する、キャッシュされたデータベース構造のメモリ内アドレス。|  
|**artcache_table_address**|**varbinary(8)**|パブリッシュされたテーブル アーティクルに関する、キャッシュされたテーブル構造のメモリ内アドレス。|  
|**artcache_schema_address**|**varbinary(8)**|パブリッシュされたテーブル アーティクルに関する、キャッシュされたアーティクル スキーマ構造のメモリ内アドレス。|  
|**artcache_article_address**|**varbinary(8)**|パブリッシュされたテーブル アーティクルに関する、キャッシュされたアーティクル構造のメモリ内アドレス。|  
|**artid**|**bigint**|このテーブル内にある各エントリの一意識別子。|  
|**artfilter**|**bigint**|アーティクルを行方向へフィルター選択する場合に使用されるストアド プロシージャの ID。|  
|**artobjid**|**bigint**|パブリッシュされたオブジェクトの ID。|  
|**artpubid**|**bigint**|アーティクルが属するパブリケーションの ID。|  
|**artstatus**|**tinyint**|アーティクル オプションおよび状態のビットマスク。次の 1 つ以上の値の、ビットごとの論理和の結果になります。<br /><br /> **1** = アーティクルはアクティブです。<br /><br /> **8** = INSERT ステートメントに列名を含みます。<br /><br /> **16** = ステートメント パラメーターを使用します。<br /><br /> **24** = 両方の INSERT ステートメントに列名を含めるし、パラメーター化されたステートメントを使用します。<br /><br /> たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクルの場合、この列の値は 17 になります。 値 0 は、アーティクルが非アクティブであり、追加のプロパティが定義されていないことを表します。|  
|**arttype**|**tinyint**|アーティクルの種類。<br /><br /> **1**ログベースのアーティクルを = です。<br /><br /> **3** = 手動フィルター付きログベースのアーティクルです。<br /><br /> **5** = 手動ビュー付きログベースのアーティクルです。<br /><br /> **7** = 手動フィルターおよび手動ビュー付きログベースのアーティクルです。<br /><br /> **8**ストアド プロシージャの実行を = です。<br /><br /> **24**シリアル化可能なストアド プロシージャの実行を = です。<br /><br /> **32** = ストアド プロシージャ (スキーマのみ)。<br /><br /> **64** = ビュー (スキーマのみ)。<br /><br /> **128** = 関数 (スキーマのみ)。|  
|**wszArtdesttable**|**nvarchar(514)**|パブリッシュ先での、パブリッシュされたオブジェクトの名前。|  
|**wszArtdesttableowner**|**nvarchar(514)**|パブリッシュ先での、パブリッシュされたオブジェクトの所有者。|  
|**wszArtinscmd**|**nvarchar(510)**|挿入に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypeIns**|**int**|挿入ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **1**呼び出しを =<br /><br /> **2** = SQL<br /><br /> **3** = なし<br /><br /> **7** = UNKNOWN|  
|**wszArtdelcmd**|**nvarchar(510)**|削除に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypeDel**|**int**|削除ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **0** XCALL を =<br /><br /> **1**呼び出しを =<br /><br /> **2** = SQL<br /><br /> **3** = なし<br /><br /> **7** = UNKNOWN|  
|**wszArtupdcmd**|**nvarchar(510)**|更新に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypeUpd**|**int**|更新ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **0** XCALL を =<br /><br /> **1**呼び出しを =<br /><br /> **2** = SQL<br /><br /> **3** = なし<br /><br /> **4** MCALL を =<br /><br /> **5** VCALL を =<br /><br /> **6** SCALL を =<br /><br /> **7** = UNKNOWN|  
|**wszArtpartialupdcmd**|**nvarchar(510)**|部分更新に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypePartialUpd**|**int**|部分更新ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **2** = SQL|  
|**numcol**|**int**|列方向にフィルター選択されたアーティクルのパーティション内の列数。|  
|**artcmdtype**|**tinyint**|現在レプリケートされているコマンドの種類。次のいずれかになります。<br /><br /> **1**挿入を =<br /><br /> **2** = DELETE<br /><br /> **3**更新プログラムを =<br /><br /> **4** = UPDATETEXT<br /><br /> **5** = なし<br /><br /> **6** = 内部使用のみ<br /><br /> **7** = 内部使用のみ<br /><br /> **8** = 部分的な更新|  
|**artgeninscmd**|**nvarchar(510)**|アーティクルに含まれる列に基づく INSERT コマンド テンプレート。|  
|**artgendelcmd**|**nvarchar(510)**|DELETE コマンド テンプレート。呼び出し構文が使用されているかどうかに基づいて、アーティクル内にある主キーまたは列が含まれます。|  
|**artgenupdcmd**|**nvarchar(510)**|UPDATE コマンド テンプレート。呼び出し構文が使用されているかどうかに基づいて、主キー、更新された列、または完全な列リストが含まれます。|  
|**artpartialupdcmd**|**nvarchar(510)**|部分 UPDATE コマンド テンプレート。主キーと更新された列が含まれます。|  
|**artupdtxtcmd**|**nvarchar(510)**|UPDATETEXT コマンド テンプレート。主キーと更新された列が含まれます。|  
|**artgenins2cmd**|**nvarchar(510)**|同時実行スナップショットの処理中、アーティクルを調整する場合に使用される、INSERT コマンド テンプレート。|  
|**artgendel2cmd**|**nvarchar(510)**|同時実行スナップショットの処理中、アーティクルを調整する場合に使用される、DELETE コマンド テンプレート。|  
|**fInReconcile**|**tinyint**|同時実行スナップショットの処理中に、アーティクルが現在調整されているかどうかを示します。|  
|**fPubAllowUpdate**|**tinyint**|パブリケーションがサブスクリプションの更新を許可するかどうかを示します。|  
|**intPublicationOptions**|**bigint**|ビットごとのオプションの値が、追加の発行オプションを指定するビットマップ。<br /><br /> **0x1** - ピア ツー ピア レプリケーションに対して有効です。<br /><br /> **0x2** -ローカル変更のみをパブリッシュします。<br /><br /> **0x4**の SQL Server 以外のサブスクライバーに対応します。|  
  
## <a name="permissions"></a>権限  
 呼び出す、パブリケーション データベースに対する VIEW DATABASE STATE 権限が必要**dm_repl_articles**です。  
  
## <a name="remarks"></a>解説  
 返される情報は、レプリケーション アーティクル キャッシュに現在読み込まれている、レプリケートされたデータベース オブジェクトの情報だけです。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [レプリケーション関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  

