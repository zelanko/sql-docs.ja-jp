---
title: sys.syscolumns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-enginel, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 935b76922ec40b8bdca28a0766e4c5b7c3d8754a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830030"
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  すべてのテーブルおよびビューの各列、およびデータベース内のストアド プロシージャのパラメーターごとに 1 行のデータを返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|列またはプロシージャ パラメーターの名前。|  
|**id**|**int**|この列が所属するテーブルのオブジェクト ID またはこのパラメーターが使用されているストアド プロシージャの ID です。|  
|**xtype**|**tinyint**|物理記憶型**sys.types**します。|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|拡張ユーザー定義データ型の ID です。 データ型の数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**length**|**smallint**|最大物理記憶長**sys**.**型**します。|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**smallint**|列またはパラメーターの ID です。|  
|**xoffset**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|この列の既定の ID です。|  
|**domain**|**int**|ルールまたはこの列の CHECK 制約の ID。|  
|**number**|**smallint**|グループ化しているプロシージャの場合は、サブプロシージャ番号です。<br /><br /> 0 = プロシージャ以外のエントリ|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary(8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**smallint**|この列が表示される行に対するオフセットです。|  
|**collationid**|**int**|列の照合順序の ID です。 文字ベース以外の列の場合は、NULL です。|  
|**status**|**tinyint**|列またはパラメーターのプロパティを説明するビットマップです。<br /><br /> 0x08 = NULL 入力を許可する列です。<br /><br /> 0x10 = ANSI による埋め込みがとき**varchar**または**varbinary**列が追加されました。 末尾の空白が保持されます**varchar**後続のゼロが保持される**varbinary**列。<br /><br /> 0x40 = OUTPUT パラメーターです。<br /><br /> 0x80 = ID 列です。|  
|**type**|**tinyint**|物理記憶型**sys**.**型**します。|  
|**usertype**|**smallint**|ユーザー定義データ型の ID **sys.types**します。 データ型の数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|この列の有効桁数のレベルです。<br /><br /> -1 = **xml**または大きな値の型。|  
|**scale**|**int**|この列の小数点以下桁数。<br /><br /> NULL = データ型は数値型以外です。|  
|**iscomputed**|**int**|列が計算列かどうかを示すフラグを設定します。<br /><br /> 0 = 非計算列<br /><br /> 1 = 計算列|  
|**isoutparam**|**int**|プロシージャ パラメーターが出力パラメーターかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**isnullable**|**int**|列が NULL 値を許容するかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**collation**|**sysname**|列の照合順序の名前です。 文字ベースの列ではない場合は NULL です。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
