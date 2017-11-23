---
title: "IHsyscolumns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs: TSQL
helpviewer_keywords: IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 347a3b691f2933cc4e3fbedcb3ddb59171da0108
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHsyscolumns**ビューから、SQL Server 以外のパブリッシャーがパブリッシュされるアーティクルの列情報を公開します。 このビューは、distributiondatabase に格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|列またはプロシージャ パラメーターの名前です。|  
|**id**|**int**|この列が所属するテーブルのオブジェクト ID、またはこのパラメーターが使用されているストアド プロシージャの ID です。|  
|**xtype**|**tinyint**|物理記憶型[sys.systypes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|拡張ユーザー定義データ型の ID。|  
|**長さ**|**bigint**|最大物理記憶長[sys.systypes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**返された colid**|**int**|列またはパラメーターの id。|  
|**x オフセット**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**予約されています**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|この列の既定の ID。|  
|**ドメイン**|**int**|この列のルールまたは CHECK 制約の ID です。|  
|**数**|**int**|プロシージャがグループ化されている場合は、サブプロシージャ番号 (**0**プロシージャ以外のエントリ)。|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**オフセット**|**int**|この列が表示される行へのオフセット。|  
|**collationid**|**int**|列の照合順序の ID。 列に基づく文字以外の場合は NULL です。|  
|**言語**|**int**|列の言語識別子です。|  
|**ステータス**|**int**|列またはパラメーターのプロパティを説明するために使用するビットマップ。<br /><br /> **0x08** = 列は null 値を許可します。<br /><br /> **0x10** = ANSI による埋め込みが効果的とき**varchar**または**varbinary**列が追加されました。 末尾の空白を保持しつつ**varchar**の後続のゼロが保持されるので**varbinary**列です。<br /><br /> **0x40** = パラメーターは出力パラメーターです。<br /><br /> **0x80** = 列が id 列です。|  
|**型**|**int**|物理記憶型[sys.systypes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**usertype**|**tinyint**|ユーザー定義データ型の ID [sys.systypes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**int**|この列の有効桁数のレベルです。|  
|**小数点以下桁数**|**int**|この列の小数点以下桁数です。|  
|**[iscomputed]**|**int**|列が計算列であるかどうかを示すフラグです。<br /><br /> **0** = 計算します。<br /><br /> **1** = 計算します。|  
|**isoutparam**|**int**|プロシージャ パラメーターが出力パラメーターかどうかを示します。<br /><br /> **1** = true です。<br /><br /> **0** = false。|  
|**isnullable**|**int**|列が NULL 値を許容するかどうかを示します。<br /><br /> **1** = true です。<br /><br /> **0** = false。|  
|**照合順序**|**int**|列の照合順序の名前。 列に基づく文字以外の場合は NULL です。|  
|**tdscollation**|**int**|表形式のデータ ストリーム (TDS) で返された場合の列の照合順序の名前です。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
