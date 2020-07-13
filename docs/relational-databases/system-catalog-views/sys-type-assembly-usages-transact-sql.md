---
title: type_assembly_usages (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.type_assembly_usages
- sys.type_assembly_usages_TSQL
- type_assembly_usages_TSQL
- type_assembly_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.type_assembly_usages catalog view
ms.assetid: 79b8bf25-6e4e-4a07-ae93-7a4e44f65171
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 65acbc32713b6aab432deac0941081e05836d677
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895896"
---
# <a name="systype_assembly_usages-transact-sql"></a>type_assembly_usages (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  アセンブリ参照への型ごとに1行の値を格納します。  
  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**user_type_id**|**int**|種類の ID です。<br /><br /> 型の名前を返すには、この列の[型](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)のカタログビューに結合します。|  
|**assembly_id**|**int**|アセンブリの ID|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;スカラー型のカタログビュー](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
