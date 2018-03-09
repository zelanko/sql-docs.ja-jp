---
title: "TABLE_PRIVILEGES (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TABLE_PRIVILEGES_TSQL
- TABLE_PRIVILEGES
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.TABLE_PRIVILEGES view
- TABLE_PRIVILEGES view
ms.assetid: 70269d26-b085-4a98-8a9f-b4742c2848bd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d710b2318a52d307facd37bbd6b03a8c22e54d69
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tableprivileges-transact-sql"></a>TABLE_PRIVILEGES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースにおける現在のユーザーに与えられたテーブル特権、またはこのユーザーが与えるテーブル特権ごとに、1 行のデータを返します。  
  
 これらのビューから情報を取得するには、完全修飾の名前を指定**INFORMATION_SCHEMA** 。*view_name*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**権限の許可者**|**nvarchar (**128**)**|特権の設定者です。|  
|**権限付与対象ユーザー**|**nvarchar (**128**)**|特権の被設定者です。|  
|**TABLE_CATALOG**|**nvarchar (**128**)**|テーブル修飾子|  
|**TABLE_SCHEMA、**|**nvarchar (**128**)**|テーブルを含むスキーマの名前<br /><br /> **\*\*重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**sysname**|テーブル名です。|  
|**PRIVILEGE_TYPE**|**varchar (**10**)**|特権のタイプです。|  
|**IS_GRANTABLE**|**varchar (**3**)**|被設定者が別の人に権限を許可できるかどうかを示します。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;です。TRANSACT-SQL と #41 です。](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [sys.server_permissions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)  
  
  
