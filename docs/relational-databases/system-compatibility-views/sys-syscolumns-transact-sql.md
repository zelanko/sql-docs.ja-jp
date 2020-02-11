---
title: syscolumns (Transact-sql) |Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c158533188db7e3d72235a69bff1b14546a1a1a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089238"
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  すべてのテーブルおよびビューのすべての列に対して1行、およびデータベース内のストアドプロシージャ内の各パラメーターの行を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|列またはプロシージャパラメーターの名前。|  
|**番号**|**int**|この列が所属するテーブルのオブジェクト ID またはこのパラメーターが使用されているストアド プロシージャの ID です。|  
|**xtype**|**tinyint**|**Sys. 型**からの物理ストレージ型。|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|拡張ユーザー定義データ型の ID。 データ型の数が32767を超えた場合、オーバーフローまたは NULL を返します。|  
|**数**|**smallint**|**Sys**からの最大物理ストレージ長。**型**。|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**smallint**|列またはパラメーター ID。|  
|**xoffset**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**確保**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|この列の既定値の ID。|  
|**領域**|**int**|この列のルールまたは CHECK 制約の ID。|  
|**number**|**smallint**|グループ化しているプロシージャの場合は、サブプロシージャ番号です。<br /><br /> 0 = プロシージャ以外のエントリ|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary (8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**影**|**smallint**|この列が表示される行にオフセットします。|  
|**collationid**|**int**|列の照合順序の ID。 非文字ベースの列の場合は NULL です。|  
|**オンライン**|**tinyint**|列またはパラメーターのプロパティを説明するビットマップです。<br /><br /> 0x08 = NULL 入力を許可する列です。<br /><br /> 0x10 = **varchar**または**varbinary**列が追加されたときに、ANSI padding が有効になりました。 **Varchar**の後続の空白は保持され、 **varbinary**列の後続のゼロは保持されます。<br /><br /> 0x40 = OUTPUT パラメーターです。<br /><br /> 0x80 = 列は ID 列です。|  
|**type**|**tinyint**|**Sys**からの物理ストレージの種類。**型**。|  
|**usertype**|**smallint**|**Sys. 型**からのユーザー定義データ型の ID。 データ型の数が32767を超えた場合、オーバーフローまたは NULL を返します。|  
|**printfmt**|**varchar (255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|この列の有効桁数。<br /><br /> -1 = **xml**または大きな値の型。|  
|**scale**|**int**|この列の小数点以下桁数。<br /><br /> NULL = データ型は数値型ではありません。|  
|**iscomputed**|**int**|列が計算されるかどうかを示すフラグです。<br /><br /> 0 = 非計算列<br /><br /> 1 = 計算列|  
|**isoutparam**|**int**|プロシージャパラメーターが出力パラメーターかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**isnullable**|**int**|列が NULL 値を許容するかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**規則**|**sysname**|列の照合順序の名前です。 文字ベースの列ではない場合は NULL です。|  
  
## <a name="see-also"></a>参照  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-sql&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
