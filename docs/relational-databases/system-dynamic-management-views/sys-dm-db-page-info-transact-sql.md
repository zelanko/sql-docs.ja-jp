---
title: sys.dm_db_page_info (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_page_info
- sys.dm_db_page_info_TSQL
- dm_db_page_info
- dm_db_page_info_TSQL
- dbcc page
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_page_info dynamic management view
author: ''
ms.author: pamela
manager: amitban
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9f2e2d0b49f58eff2eac52103bddc6fda818aeb3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849281"
---
# <a name="sysdmdbpageinfo-transact-sql"></a>sys.dm_db_page_info (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

データベース内のページに関する情報を返します。  ページで、ヘッダー情報を含む 1 つの行を返しますなど、 `object_id`、 `index_id`、および`partition_id`します。  この関数を使用する必要が置き換えられます`DBCC PAGE`ほとんどの場合。

## <a name="syntax"></a>構文  
  
```  
sys.dm_db_page_info ( DatabaseId, FileId, PageId, Mode )  
``` 

## <a name="arguments"></a>引数  
 *DatabaseId* |NULL |既定値  

 データベースの ID です。 *DatabaseId*は**smallint**します。 有効な入力は、データベースの ID 番号です。 既定では null の場合、ただし送信このパラメーターの NULL 値がエラーになります。
 
*FileId* |NULL |既定値

ファイルの ID を指定します。 *FileId*は**int**します。有効な入力で指定されたデータベース内のファイルの ID 番号は、 *DatabaseId*します。 既定では null の場合、ただし送信このパラメーターの NULL 値がエラーになります。

*PageId* |NULL |既定値

ページの ID です。  *PageId*は**int**します。有効な入力で指定されたファイル内のページの ID 番号は、 *FileId*します。 既定では null の場合、ただし送信このパラメーターの NULL 値がエラーになります。

*モード*|NULL |既定値

関数の出力の詳細のレベルを決定します。 '制限' はすべての説明列に NULL 値を返しますには、'詳細'、列の説明を入力します。  既定値は '制限されています '。

## <a name="table-returned"></a>返されるテーブル  

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id |ssNoversion |データベース ID |
|file_id |ssNoversion |ファイル ID |
|page_id |ssNoversion |ページ ID |
|page_type |ssNoversion |ページの種類 |
|page_type_desc |nvarchar(64) |ページの種類の説明 |
|page_flag_bits |nvarchar(64) |ページ ヘッダー フラグのビット |
|page_flag_bits_desc |nvarchar (256) |ページ ヘッダー フラグ ビット説明 |
|page_type_flag_bits |nvarchar(64) |ページ ヘッダーの型のフラグのビット |
|page_type_flag_bits_desc |nvarchar(64) |ページ ヘッダー内の型フラグのビットの説明 |
|object_id |ssNoversion |ページを所有するオブジェクトの ID |
|index_id |ssNoversion |インデックス (ヒープ データ ページの場合は 0) の ID |
|partition_id |BIGINT |パーティションの ID |
|alloc_unit_id |BIGINT |アロケーション ユニットの ID |
|page_level |ssNoversion |インデックスのページのレベル (リーフ = 0) |
|slot_count |SMALLINT |スロット数の合計 (使用済みおよび未使用) <br> データ ページでは、この値は行の数に相当します。 |
|ghost_rec_count |SMALLINT |ページ上のゴーストとしてマークされたレコードの数 <br> ゴースト レコードは、削除対象としてマークされていますが、削除するのにはまだ 1 つです。 |
|torn_bits |ssNoversion |データの欠落を検出するためのセクターごとに 1 ビット。 チェックサムの格納にも使用 <br> この値は、データの破損を検出するために使用されます。 |
|is_iam_pg |bit |ページが IAM ページかどうかを示すビット  |
|is_mixed_ext |bit |指定する場合にビット混合エクステントの割り当てください。 |
|pfs_file_id |SMALLINT |対応する PFS ページのファイル ID |
|pfs_page_id |ssNoversion |対応する PFS ページのページ ID |
|pfs_alloc_percent |ssNoversion |PFS バイトで示されている割り当て % |
|pfs_status |nvarchar(64) |PFS バイト |
|pfs_status_desc |nvarchar(64) |PFS バイトの説明 |
|gam_file_id |SMALLINT |対応する GAM ページのファイル ID |
|gam_page_id |ssNoversion |対応する GAM ページのページ ID |
|gam_status |bit |GAM に割り当てられた指定する場合のビット |
|gam_status_desc |nvarchar(64) |状態の GAM のビットの説明 |
|sgam_file_id |SMALLINT |ファイルの対応する SGAM ページの ID |
|sgam_page_id |ssNoversion |対応する SGAM ページのページ ID |
|sgam_status |bit |SGAM で割り当てを指定する場合にビット |
|sgam_status_desc |nvarchar(64) |状態の SGAM のビットの説明 |
|diff_map_file_id |SMALLINT |対応する差分ビットマップ ページのファイル ID |
|diff_map_page_id |ssNoversion |対応する差分ビットマップ ページのページ ID |
|diff_status |bit |差分の状態が変更されたかどうかを示すビット |
|diff_status_desc |nvarchar(64) |差分の状態のビットの説明 |
|ml_file_id |SMALLINT |最小ログ記録ビットマップの該当するページのファイル ID |
|ml_page_id |ssNoversion |最小ログ記録ビットマップの該当するページのページ ID |
|ml_status |bit |ビットを示すかどうか、ページは、最小ログ記録 |
|ml_status_desc |nvarchar(64) |ビットが最小ログ記録の状態の説明 |
|free_bytes |SMALLINT |ページ上の空きバイト数 |
|free_data_offset |ssNoversion |データ領域の最後に空き領域のオフセットします。 |
|reserved_bytes |SMALLINT |すべてのトランザクションによって予約された空きバイト数 (場合ヒープ) <br> (インデックスのリーフ) の場合、非実体行の数 |
|reserved_xdes_id |SMALLINT |M_xdesID m_reservedCnt に起因する領域 <br> デバッグの目的でのみ |
|xdes_id |nvarchar(64) |M_reserved から提供された最新のトランザクション <br> デバッグの目的でのみ |
|prev_page_file_id |SMALLINT |前のページのファイル ID |
|prev_page_page_id |ssNoversion |前のページのページ ID |
|next_page_file_id |SMALLINT |次のページのファイル ID |
|next_page_page_id |ssNoversion |次のページのページ ID |
|min_len |SMALLINT |固定サイズの行の長さ |
|lsn |nvarchar(64) |ログ シーケンス番号/タイムスタンプ |
|header_version |ssNoversion |ページ ヘッダーのバージョン |

## <a name="remarks"></a>コメント
`sys.dm_db_page_info`動的管理関数のようなページの情報を返します`page_id`、 `file_id`、 `index_id`、`object_id`ページ ヘッダーに存在するなど。 この情報は、トラブルシューティングとさまざまなパフォーマンス (ロックとラッチの競合) や破損の問題をデバッグする場合に便利です。

`sys.dm_db_page_info` 代わりに使用できる、`DBCC PAGE`ステートメントが、多くの場合にのみページ ヘッダーの情報を返します、ページの本文ではありません。 `DBCC PAGE` ページの内容全体が必要なユース ケースにも必要になります。

## <a name="using-in-conjunction-with-other-dmvs"></a>その他の Dmv と組み合わせて使用します。
1 つの重要なユース ケースの`sys.dm_db_page_info`にページの情報を公開するその他の Dmv を使用したことを参加させます。  このユース ケースを容易にする新しい列と呼ばれる`page_resource`8 バイトの 16 進形式でページの情報を表示する追加されています。 この列が追加されました`sys.dm_exec_processes`と`sys.sysprocesses`し、必要に応じて、将来の他の Dmv に追加されます。

新しい関数の場合、 `sys.fn_PageResCracker`、受け取り、`page_resource`入力し、出力を含む単一行として`database_id`、`file_id`と`page_id`します。  この関数は、間の結合を容易にし、使用できます`sys.dm_exec_requests`または`sys.sysprocesses`と`sys.dm_db_page_info`します。

## <a name="permissions"></a>アクセス許可  
必要があります、`VIEW DATABASE STATE`データベースの権限。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-all-the-properties-of-a-page"></a>A. ページのすべてのプロパティを表示します。
次のクエリが 1 つの行のすべてのページの情報を返します、指定された`database_id`、 `file_id`、`page_id`既定のモード (限定) と組み合わせて

```sql
SELECT *  
FROM sys.dm_db_page_info (5, 1, 15, DEFAULT)
```

### <a name="b-using-sysdmdbpageinfo-with-other-dmvs"></a>B. その他の Dmv を使用した sys.dm_db_page_info を使用します。 

次のクエリごとに 1 行を返します`wait_resource`によって公開される`sys.dm_exec_requests`行が null 以外に含まれる場合 `page_resource`

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```

## <a name="see-also"></a>参照  
[動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_exec_requests (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   


