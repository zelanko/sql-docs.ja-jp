---
title: COLUMN_PRIVILEGES (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- COLUMN_PRIVILEGES
- COLUMN_PRIVILEGES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- COLUMN_PRIVILEGES view
- INFORMATION_SCHEMA.COLUMN_PRIVILEGES view
ms.assetid: 8ae29a85-2b77-48db-a2b9-a1720287b271
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c5c56c3d07a6600b28bbb15e5fe042d9f2ddfe97
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822167"
---
# <a name="columnprivileges-transact-sql"></a>COLUMN_PRIVILEGES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースにおける現在のユーザーに与えられた特権、またはこのユーザーが与える特権を持つ列ごとに、1 行のデータを返します。  
  
 これらのビューから情報を取得するには、完全修飾名を指定 **INFORMATION_SCHEMA. * * * view_name*します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**権限の許可者**|**nvarchar(** 128 **)**|特権の設定者です。|  
|**権限付与対象ユーザー**|**nvarchar(** 128 **)**|特権の被設定者です。|  
|**TABLE_CATALOG**|**nvarchar(** 128 **)**|テーブル修飾子|  
|**TABLE_SCHEMA**|**nvarchar(** 128 **)**|テーブルを含むスキーマの名前<br /><br /> **\*\* 重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**sysname**|テーブル名です。|  
|**COLUMN_NAME**|**sysname**|列名|  
|**PRIVILEGE_TYPE**|**varchar (** 10 **)**|特権のタイプです。|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|被設定者が別の人に権限を許可できるかどうかを示します。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;TRANSACT-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [sys.server_permissions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)  
  
  
