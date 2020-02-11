---
title: sys. スキーマ (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f5a0707c599b70ec3c006b00eacb5f8c1a8a87b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018343"
---
# <a name="schemas-catalog-views---sysschemas"></a>スキーマカタログビュー-sys スキーマ
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  データベーススキーマごとに1行のデータを格納します。  
  
> [!NOTE]  
>  データベース スキーマは、XML ドキュメントのコンテンツ モデルの定義に使用される XML スキーマとは異なります。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|スキーマの名前。 データベース内で一意です。|  
|**schema_id**|**int**|スキーマの ID です。 データベース内で一意です。|  
|**principal_id**|**int**|このスキーマを所有するプリンシパルの ID。|  
  
## <a name="remarks"></a>解説  
データベーススキーマは、テーブル、ビュー、プロシージャ、関数など、オブジェクトの名前空間またはコンテナーとして機能します。これは、**のカタログビュー**にあります。  

各スキーマには所有者があります。 所有者はセキュリティ[プリンシパル](../../relational-databases/security/authentication-access/principals-database-engine.md)です。
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。 詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[プリンシパル](../../relational-databases/security/authentication-access/principals-database-engine.md)

[カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   

[スキーマカタログビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   

[sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
