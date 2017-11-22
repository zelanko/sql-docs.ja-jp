---
title: "sys.systypes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.systypes_TSQL
- systypes_TSQL
- sys.systypes
- systypes
dev_langs: TSQL
helpviewer_keywords:
- sys.systypes compatibility view
- systypes system table
ms.assetid: 1b0b1d0c-5f7b-470b-bd52-8bfa922d7889
caps.latest.revision: "50"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b505bed051d34e8cdd4237fa3cb73e15f1fd0b2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syssystypes-transact-sql"></a>sys.systypes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースで定義されている、システムから提供されているデータ型およびユーザー定義データ型ごとに 1 行のデータを返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|データ型の名前です。|  
|**xtype**|**tinyint**|物理記憶型です。|  
|**ステータス**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|拡張ユーザー タイプです。 データ型の数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**長さ**|**smallint**|データ型の物理的な長さです。|  
|**xprec**|**tinyint**|サーバーが使用する内部の有効桁数です。 クエリでは使用されません。|  
|**xscale**|**tinyint**|サーバーが使用する内部の小数点以下桁数です。 クエリでは使用されません。|  
|**%t**|**int**|このデータ型の整合性チェックを行うストアド プロシージャの ID です。|  
|**ドメイン**|**int**|このデータ型の整合性チェックを行うストアド プロシージャの ID です。|  
|**uid**|**smallint**|型の所有者のスキーマ ID です。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の前のバージョンからアップグレードしたデータベースの場合、スキーマ ID は所有者のユーザー ID と同じです。<br /><br /> **\*\*重要な\* \*** 場合は、次のいずれかを使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DDL ステートメントを使用する必要がある、 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログ ビューの代わりに**sys.systypes**.<br /><br /> ALTER AUTHORIZATION ON TYPE<br /><br /> CREATE TYPE<br /><br /> ユーザーとロールの数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**予約されています**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**collationid**|**int**|文字ベースの場合**collationid**現在のデータベースの照合順序の id は、それ以外の場合は NULL です。|  
|**usertype**|**smallint**|ユーザー型の ID です。 データ型の数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|**変数**|**bit**|可変長データ型です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**null を許容**|**bit**|既定で NULL 値を許容するかどうかを示します。 使用して null 値許容属性が指定されている場合、この既定値はによってオーバーライド[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)または[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。|  
|**型**|**tinyint**|物理記憶データ型です。|  
|**printfmt**|**varchar (255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|このデータ型の有効桁数です。<br /><br /> -1 = **xml**または大きな値の型。|  
|**小数点以下桁数**|**tinyint**|このデータ型の有効桁数に基づく小数点以下桁数です。<br /><br /> NULL = データ型は数値型以外です。|  
|**照合順序**|**sysname**|文字ベースの場合**照合**現在のデータベースの照合順序は、それ以外の場合は NULL です。|  
  
## <a name="see-also"></a>参照  
 [互換性ビュー &#40;です。TRANSACT-SQL と #41 です。](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
