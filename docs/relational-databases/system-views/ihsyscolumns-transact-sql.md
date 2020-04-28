---
title: IHsyscolumns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: a432685809676f997049940ea5aa1ce43dc38a60
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029629"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHsyscolumns**ビューは、SQL Server 以外のパブリッシャーからパブリッシュされたアーティクルの列情報を公開します。 このビューは、このデータベースに格納されています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|列またはプロシージャ パラメーターの名前です。|  
|**id**|**int**|この列が所属するテーブルのオブジェクト ID、またはこのパラメーターが使用されているストアド プロシージャの ID です。|  
|**xtype**|**tinyint**|Systypes の物理ストレージの種類は、 [transact-sql&#41;&#40;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)ます。|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|拡張ユーザー定義データ型の ID です。|  
|**length**|**bigint**|Systypes からの最大物理ストレージ長は、 [transact-sql&#41;&#40;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)です。|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**int**|列またはパラメーター ID。|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**確保**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|この列の既定の ID。|  
|**領域**|**int**|この列のルールまたは CHECK 制約の ID。|  
|**number**|**int**|プロシージャがグループ化されたときのサブプロシージャ番号 (プロシージャ以外のエントリの場合は**0** )。|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|この列が表示される行のオフセット。|  
|**collationid**|**int**|列の照合順序の ID。 文字ベース以外の列の場合は NULL です。|  
|**言語**|**int**|列の言語識別子。|  
|**status**|**int**|列またはパラメーターのプロパティを記述するために使用されるビットマップ。<br /><br /> **0x08** = 列は null 値を許容します。<br /><br /> **0x10** = **varchar**または**varbinary**列が追加されたときに、ANSI padding が有効になりました。 **Varchar**の後続の空白は保持され、 **varbinary**列の後続のゼロは保持されます。<br /><br /> **0x40** = パラメーターは出力パラメーターです。<br /><br /> **0x80** = 列は id 列です。|  
|**type**|**int**|Systypes の物理ストレージの種類は、 [transact-sql&#41;&#40;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)ます。|  
|**usertype**|**tinyint**|Systypes からのユーザー定義データ型の ID [&#40;transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)。|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**int**|この列の有効桁数です。|  
|**scale**|**int**|この列の小数点以下桁数です。|  
|**iscomputed**|**int**|列が計算されるかどうかを示すフラグ。<br /><br /> **0** = 非計算。<br /><br /> **1** = 計算済み。|  
|**isoutparam**|**int**|プロシージャパラメーターが出力パラメーターかどうかを示します。<br /><br /> **1** = True。<br /><br /> **0** = False。|  
|**isnullable**|**int**|列が NULL 値を許容するかどうかを示します。<br /><br /> **1** = True。<br /><br /> **0** = False。|  
|**規則**|**int**|列の照合順序の名前。 文字ベース以外の列の場合は NULL です。|  
|**tdscollation**|**int**|表形式のデータ ストリーム (TDS) で返された場合の列の照合順序の名前です。|  
  
## <a name="see-also"></a>参照  
 [異種データベースレプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
