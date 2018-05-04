---
title: sys.dm_repl_schemas (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_repl_schemas_TSQL
- dm_repl_schemas
- sys.dm_repl_schemas_TSQL
- sys.dm_repl_schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_schemas dynamic management function
ms.assetid: 6f5fefff-8492-4360-bd5b-a97287367914
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f1ae6561bc96f5d4dff4d21a6057a4c1b9816c4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmreplschemas-transact-sql"></a>sys.dm_repl_schemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーションでパブリッシュされたテーブル列に関する情報を返します。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artcache_schema_address**|**varbinary(8)**|パブリッシュされたテーブル アーティクルに関する、キャッシュされたスキーマ構造のメモリ内アドレス。|  
|**tabid**|**bigint**|レプリケートされたテーブルの ID。|  
|**indexid**|**smallint**|パブリッシュされたテーブルのクラスター化インデックスの ID。|  
|**idSch**|**bigint**|テーブル スキーマの ID。|  
|**tabschema**|**nvarchar(510)**|テーブル スキーマの名前。|  
|**ccTabschema**|**smallint**|テーブル スキーマの文字長。|  
|**tabname**|**nvarchar(510)**|パブリッシュされたテーブルの名前。|  
|**ccTabname**|**smallint**|パブリッシュされたテーブル名の文字長。|  
|**rowsetid_delete**|**bigint**|削除された行の ID。|  
|**rowsetid_insert**|**bigint**|挿入された行の ID。|  
|**num_pk_cols**|**int**|主キー列の数。|  
|**pcitee**|**binary(8000)**|計算列の評価に使用するクエリ式構造へのポインター。|  
|**re_numtextcols**|**int**|レプリケートされたテーブルのバイナリ ラージ オブジェクト列の数。|  
|**re_schema_lsn_begin**|**binary(8000)**|スキーマ バージョンのログ記録に関する最初のログ シーケンス番号 (LSN)。|  
|**re_schema_lsn_end**|**binary(8000)**|スキーマ バージョンのログ記録に関する最後の LSN。|  
|**re_numcols**|**int**|パブリッシュされた列の数。|  
|**re_colid**|**int**|パブリッシャーの列識別子。|  
|**re_awcName**|**nvarchar(510)**|パブリッシュされた列の名前。|  
|**re_ccName**|**smallint**|列名の文字数。|  
|**re_pk**|**tinyint**|パブリッシュされた列が主キーの一部かどうかを示します。|  
|**re_unique**|**tinyint**|パブリッシュされた列が一意のインデックスの一部かどうかを示します。|  
|**re_maxlen**|**smallint**|パブリッシュされた列の最大長。|  
|**re_prec**|**tinyint**|パブリッシュされた列の有効桁数。|  
|**re_scale**|**tinyint**|パブリッシュされた列の小数点以下桁数。|  
|**re_collatid**|**bigint**|パブリッシュされた列の照合順序 ID。|  
|**re_xvtype**|**smallint**|パブリッシュされた列の型。|  
|**re_offset**|**smallint**|パブリッシュされた列のオフセット。|  
|**re_bitpos**|**tinyint**|パブリッシュされた列のバイト ベクターでのビット位置。|  
|**re_fNullable**|**tinyint**|パブリッシュされた列で NULL 値がサポートされるかどうかを示します。|  
|**re_fAnsiTrim**|**tinyint**|パブリッシュされた列で ANSI 切り捨てが使用されるかどうかを示します。|  
|**re_computed**|**smallint**|パブリッシュされた列が計算列かどうかを示します。|  
|**se_rowsetid**|**bigint**|行セットの ID。|  
|**se_schema_lsn_begin**|**binary(8000)**|スキーマ バージョンのログ記録に関する最初の LSN。|  
|**se_schema_lsn_end**|**binary(8000)**|スキーマ バージョンのログ記録に関する最後の LSN。|  
|**se_numcols**|**int**|列の数。|  
|**se_colid**|**int**|サブスクライバーでの列の ID。|  
|**se_maxlen**|**smallint**|列の最大長。|  
|**se_prec**|**tinyint**|列の有効桁数。|  
|**se_scale**|**tinyint**|列の小数点以下桁数。|  
|**se_collatid**|**bigint**|列の照合順序 ID。|  
|**se_xvtype**|**smallint**|列の型。|  
|**se_offset**|**smallint**|列のオフセット。|  
|**se_bitpos**|**tinyint**|列のバイト ベクターでのビット位置。|  
|**se_fNullable**|**tinyint**|列で NULL 値がサポートされるかどうかを示します。|  
|**se_fAnsiTrim**|**tinyint**|列で ANSI 切り捨てが使用されるかどうかを示します。|  
|**se_computed**|**smallint**|列が計算列かどうかを示します。|  
|**se_nullBitInLeafRows**|**int**|列の値が NULL かどうかを示します。|  
  
## <a name="permissions"></a>権限  
 呼び出す、パブリケーション データベースに対する VIEW DATABASE STATE 権限が必要**dm_repl_schemas**です。  
  
## <a name="remarks"></a>解説  
 返される情報は、レプリケーション アーティクル キャッシュに現在読み込まれている、レプリケートされたデータベース オブジェクトの情報だけです。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [レプリケーション関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  

