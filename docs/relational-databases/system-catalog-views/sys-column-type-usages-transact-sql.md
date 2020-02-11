---
title: column_type_usages (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_type_usages
- sys.column_type_usages_TSQL
- column_type_usages_TSQL
- sys.column_type_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_type_usages catalog view
ms.assetid: 1ead375e-f662-4837-903f-8947496c51e4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5dc3ff14375d0e07a1235f0ba79ed36e3e084e58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139992"
---
# <a name="syscolumn_type_usages-transact-sql"></a>column_type_usages (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザー定義型の列ごとに 1 行のデータを保持します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|この列が所属するオブジェクトの ID。|  
|**column_id**|**int**|列の ID。 は、オブジェクト内で一意です。|  
|**user_type_id**|**int**|ユーザー定義型の ID。<br /><br /> 型の名前を返すには、この列の[型](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)のカタログビューに結合します。|  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。 詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;スカラー型のカタログビュー](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
