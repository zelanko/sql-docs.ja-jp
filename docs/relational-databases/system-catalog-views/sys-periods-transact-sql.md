---
title: "sys.periods (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58e8428bc016975594105b842c75fca1304d0695
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysperiods-transact-sql"></a>sys.periods (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  期間が定義されている各テーブルの行を返します。  
  
|列ヘッダー|データ型|Description|  
|-------------------|---------------|-----------------|  
|period_type|**sysname**|期間の名前|  
|period_type_desc|**tinyint**|期間の型を表す数値。<br /><br /> 1 = システム期間|  
|object_id|**nvarchar (60)**|列の型のテキストの説明:<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|Period_type 列を含むテーブルの id|  
|start_column_id|**int**|期間下限の境界を定義する列の id|  
|end_column_id|**int**|期間の上限を定義する列の id|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)  
  
  
