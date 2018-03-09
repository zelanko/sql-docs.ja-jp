---
title: "sys.syscolumns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-enginel, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscolumns
- sys.syscolumns_TSQL
- syscolumns_TSQL
- syscolumns
dev_langs:
- TSQL
helpviewer_keywords:
- syscolumns system table
- sys.syscolumns compatibility view
ms.assetid: 863fd87b-ff33-4ac5-9aa9-df21140681da
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 15de1e84d8b3dcbe9d1949cb0ba745cfea671287
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  すべてのテーブルおよびビューの各列、およびデータベース内のストアド プロシージャのパラメーターごとに 1 行のデータを返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|列またはプロシージャ パラメーターの名前です。|  
|**id**|**int**|この列が所属するテーブルのオブジェクト ID またはこのパラメーターが使用されているストアド プロシージャの ID です。|  
|**xtype**|**tinyint**|物理記憶型**sys.types**です。|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|拡張ユーザー定義データ型の ID です。 データ型の数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**長さ**|**smallint**|最大物理記憶長**sys**.**型**です。|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**smallint**|列またはパラメーターの ID です。|  
|**xoffset**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|この列の既定の ID です。|  
|**domain**|**int**|この列に CHECK 制約、ルールの ID です。|  
|**number**|**smallint**|グループ化しているプロシージャの場合は、サブプロシージャ番号です。<br /><br /> 0 = プロシージャ以外のエントリ|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary(8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**smallint**|この列が表示される行に対するオフセットです。|  
|**collationid**|**int**|列の照合順序の ID です。 文字ベース以外の列の場合は、NULL です。|  
|**ステータス**|**tinyint**|列またはパラメーターのプロパティを説明するビットマップです。<br /><br /> 0x08 = NULL 入力を許可する列です。<br /><br /> 0x10 = ANSI による埋め込みが効果的とき**varchar**または**varbinary**列が追加されました。 末尾の空白を保持しつつ**varchar**の後続のゼロが保持されるので**varbinary**列です。<br /><br /> 0x40 = OUTPUT パラメーターです。<br /><br /> 0x80 = ID 列です。|  
|**type**|**tinyint**|物理記憶型**sys**.**型**です。|  
|**usertype**|**smallint**|ユーザー定義データ型の ID **sys.types**です。 データ型の数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|この列の有効桁数のレベルです。<br /><br /> -1 = **xml**または大きな値型です。|  
|**scale**|**int**|この列の小数点以下桁数。<br /><br /> NULL = データ型は数値型以外です。|  
|**iscomputed**|**int**|列が計算列かどうかを示すフラグを設定します。<br /><br /> 0 = 非計算列<br /><br /> 1 = 計算列|  
|**isoutparam**|**int**|プロシージャ パラメーターが出力パラメーターかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**isnullable**|**int**|列が NULL 値を許容するかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**collation**|**sysname**|列の照合順序の名前です。 文字ベースの列ではない場合は NULL です。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
