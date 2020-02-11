---
title: sys. 期間 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
author: stevestein
ms.author: sstein
ms.openlocfilehash: eea7709c67eab0dc9fe1890135f9ae03225cdff2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068091"
---
# <a name="sysperiods-transact-sql"></a>sys. 期間 (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  期間が定義されているテーブルごとに1行の値を返します。  
  
|列ヘッダー|データ型|[説明]|  
|-------------------|---------------|-----------------|  
|name|**sysname**|期間の名前|  
|period_type|**tinyint**|期間の種類を表す数値。<br /><br /> 1 = システム期間|  
|period_type_desc|**nvarchar (60)**|列の型の説明テキスト。<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|Period_type 列を含むテーブルの id|  
|start_column_id|**int**|下限の期間の境界を定義する列の id|  
|end_column_id|**int**|上限期間の境界を定義する列の id|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [system_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [SQL Server システムカタログに対するクエリについてよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)  
  
  
