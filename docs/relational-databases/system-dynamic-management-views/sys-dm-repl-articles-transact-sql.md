---
title: sys.dm_repl_articles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 65bc88be1b9a6cdb9a69d41a526916ab3aa7ab2a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031833"
---
# <a name="sysdmreplarticles-transact-sql"></a>sys.dm_repl_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション トポロジ内のアーティクルとしてパブリッシュされたデータベース オブジェクトに関する情報を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**artcache_db_address**|**varbinary(8)**|パブリケーション データベースに関する、キャッシュされたデータベース構造のメモリ内アドレス。|  
|**artcache_table_address**|**varbinary(8)**|パブリッシュされたテーブル アーティクルに関する、キャッシュされたテーブル構造のメモリ内アドレス。|  
|**artcache_schema_address**|**varbinary(8)**|パブリッシュされたテーブル アーティクルに関する、キャッシュされたアーティクル スキーマ構造のメモリ内アドレス。|  
|**artcache_article_address**|**varbinary(8)**|パブリッシュされたテーブル アーティクルに関する、キャッシュされたアーティクル構造のメモリ内アドレス。|  
|**artid**|**bigint**|このテーブル内にある各エントリの一意識別子。|  
|**artfilter**|**bigint**|アーティクルを行方向へフィルター選択する場合に使用されるストアド プロシージャの ID。|  
|**artobjid**|**bigint**|パブリッシュされたオブジェクトの ID。|  
|**artpubid**|**bigint**|アーティクルが属するパブリケーションの ID。|  
|**artstatus**|**tinyint**|アーティクル オプションおよび状態のビットマスク。次の 1 つ以上の値の、ビットごとの論理和の結果になります。<br /><br /> **1** = アーティクルはアクティブです。<br /><br /> **8** = INSERT ステートメントに列名を含みます。<br /><br /> **16** = ステートメントをパラメーター化を使用します。<br /><br /> **24** = INSERT ステートメントに列名は、どちらも、パラメーター化されたステートメントを使用しています。<br /><br /> たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクルの場合、この列の値は 17 になります。 値 0 は、アーティクルが非アクティブであり、追加のプロパティが定義されていないことを表します。|  
|**arttype**|**tinyint**|アーティクルの種類。<br /><br /> **1**ログベースのアーティクルを = です。<br /><br /> **3** = 手動フィルター付きログベースのアーティクルです。<br /><br /> **5** = 手動ビュー付きログベースのアーティクルです。<br /><br /> **7** = 手動フィルターおよび手動ビュー付きログベースのアーティクルです。<br /><br /> **8**ストアド プロシージャの実行を = です。<br /><br /> **24**シリアル化可能なストアド プロシージャの実行を = です。<br /><br /> **32** = ストアド プロシージャ (スキーマのみ)。<br /><br /> **64** = ビュー (スキーマのみ)。<br /><br /> **128** = 関数 (スキーマのみ)。|  
|**wszArtdesttable**|**nvarchar(514)**|パブリッシュ先での、パブリッシュされたオブジェクトの名前。|  
|**wszArtdesttableowner**|**nvarchar(514)**|パブリッシュ先での、パブリッシュされたオブジェクトの所有者。|  
|**wszArtinscmd**|**nvarchar(510)**|挿入に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypeIns**|**int**|挿入ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **1**呼び出しを =<br /><br /> **2** = SQL<br /><br /> **3** = なし<br /><br /> **7** = UNKNOWN|  
|**wszArtdelcmd**|**nvarchar(510)**|削除に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypeDel**|**int**|削除ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **0** XCALL を =<br /><br /> **1**呼び出しを =<br /><br /> **2** = SQL<br /><br /> **3** = なし<br /><br /> **7** = UNKNOWN|  
|**wszArtupdcmd**|**nvarchar(510)**|更新に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypeUpd**|**int**|更新ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **0** XCALL を =<br /><br /> **1**呼び出しを =<br /><br /> **2** = SQL<br /><br /> **3** = なし<br /><br /> **4** MCALL を =<br /><br /> **5** = VCALL<br /><br /> **6** SCALL を =<br /><br /> **7** = UNKNOWN|  
|**wszArtpartialupdcmd**|**nvarchar(510)**|部分更新に使用されるコマンドまたはストアド プロシージャ。|  
|**cmdTypePartialUpd**|**int**|部分更新ストアド プロシージャの呼び出し構文。次のいずれかになります。<br /><br /> **2** = SQL|  
|**numcol**|**int**|列方向にフィルター選択されたアーティクルのパーティション内の列数。|  
|**artcmdtype**|**tinyint**|現在レプリケートされているコマンドの種類。次のいずれかになります。<br /><br /> **1** = 挿入<br /><br /> **2** = DELETE<br /><br /> **3** = UPDATE<br /><br /> **4** = UPDATETEXT<br /><br /> **5** = なし<br /><br /> **6** = 内部使用のみ<br /><br /> **7** = 内部使用のみ<br /><br /> **8** = 部分的な更新|  
|**artgeninscmd**|**nvarchar(510)**|アーティクルに含まれる列に基づく INSERT コマンド テンプレート。|  
|**artgendelcmd**|**nvarchar(510)**|DELETE コマンド テンプレート。呼び出し構文が使用されているかどうかに基づいて、アーティクル内にある主キーまたは列が含まれます。|  
|**artgenupdcmd**|**nvarchar(510)**|UPDATE コマンド テンプレート。呼び出し構文が使用されているかどうかに基づいて、主キー、更新された列、または完全な列リストが含まれます。|  
|**artpartialupdcmd**|**nvarchar(510)**|部分 UPDATE コマンド テンプレート。主キーと更新された列が含まれます。|  
|**artupdtxtcmd**|**nvarchar(510)**|UPDATETEXT コマンド テンプレート。主キーと更新された列が含まれます。|  
|**artgenins2cmd**|**nvarchar(510)**|同時実行スナップショットの処理中、アーティクルを調整する場合に使用される、INSERT コマンド テンプレート。|  
|**artgendel2cmd**|**nvarchar(510)**|同時実行スナップショットの処理中、アーティクルを調整する場合に使用される、DELETE コマンド テンプレート。|  
|**fInReconcile**|**tinyint**|同時実行スナップショットの処理中に、アーティクルが現在調整されているかどうかを示します。|  
|**fPubAllowUpdate**|**tinyint**|パブリケーションがサブスクリプションの更新を許可するかどうかを示します。|  
|**intPublicationOptions**|**bigint**|ビットごとのオプションの値が、追加のパブリッシング オプションを指定するビットマップ。<br /><br /> **0x1** - ピア ツー ピア レプリケーションに対して有効です。<br /><br /> **0x2** -ローカル変更のみをパブリッシュします。<br /><br /> **0x4**の SQL Server 以外のサブスクライバーに対応します。|  
  
## <a name="permissions"></a>アクセス許可  
 呼び出すパブリケーション データベースに対する VIEW DATABASE STATE 権限が必要**dm_repl_articles**します。  
  
## <a name="remarks"></a>コメント  
 返される情報は、レプリケーション アーティクル キャッシュに現在読み込まれている、レプリケートされたデータベース オブジェクトの情報だけです。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [レプリケーション関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  

