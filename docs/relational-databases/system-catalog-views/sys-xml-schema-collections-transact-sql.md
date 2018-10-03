---
title: sys.xml_schema_collections (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_collections_TSQL
- sys.xml_schema_collections
- xml_schema_collections
- xml_schema_collections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_collections catalog view
ms.assetid: f3f7f3dc-029f-4942-ab3c-75fa9814e40f
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0e891585d5e44c4b2562d5fa704848f7abfa8292
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632580"
---
# <a name="sysxmlschemacollections-transact-sql"></a>sys.xml_schema_collections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML スキーマ コレクションごとに 1 行のデータを返します。 XML スキーマ コレクションは、名前付きの XSD 定義セットです。 XML スキーマ コレクション自体はリレーショナル スキーマに含まれ、スキーマ スコープの [!INCLUDE[tsql](../../includes/tsql-md.md)] 名で識別されます。 xml_collection_id、schema_id、および name の組は一意です。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|xml_collection_id|**int**|XML スキーマ コレクションの ID。 データベース内で一意です。|  
|schema_id|**int**|XML スキーマ コレクションを含むリレーショナル スキーマの ID。|  
|principal_id|**int**|スキーマの所有者と異なる場合は、個々 の所有者の ID。 既定では、スキーマに含まれるオブジェクトは、スキーマの所有者によって所有されます。 ただし、所有権を変更する ALTER AUTHORIZATION ステートメントを使用して、別の所有者を指定できます。<br /><br /> NULL = 別の所有者はありません。|  
|NAME|**sysname**|XML スキーマ コレクションの名前。|  
|create_date|**datetime**|XML スキーマ コレクションが作成された日付。|  
|modify_date|**datetime**|XML スキーマ コレクションが最後に変更された日付。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML スキーマ&#40;XML 型システム&#41;カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
