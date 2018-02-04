---
title: "sys.service_message_types (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.service_message_types
- service_message_types
- sys.service_message_types_TSQL
- service_message_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_message_types catalog view
ms.assetid: 6a38709a-60fe-46f6-89da-718f74f15600
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e2814cf0eaf1844131086491d1184c4f95bb52d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysservicemessagetypes-transact-sql"></a>sys.service_message_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このカタログ ビューには Service Broker に登録されたメッセージ型ごとに 1 行のデータが格納されます。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|メッセージ型の名前。データベース内で一意です。 Null を許容しません。|  
|**message_type_id**|**int**|メッセージ型の識別子。データベース内で一意です。 Null を許容しません。|  
|**principal_id**|**int**|メッセージ型を所有するデータベース プリンシパルの識別子。 NULL 値は許可されます。|  
|**validation**|**char(2)**|この型のメッセージを送信する前に、ブローカーで実行される検証。 Null を許容しません。 次のいずれかです。<br /><br /> N = なし<br /><br /> X = XML<br /><br /> E = 空|  
|**validation_desc**|**nvarchar(60)**|この型のメッセージを送信する前に、ブローカーで実行される検証の説明。 NULL 値は許可されます。 次のいずれかです。<br /><br /> なし<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|XML スキーマを使用する検証の場合、使用されるスキーマ コレクションの識別子。<br /><br /> それ以外の場合は、NULL。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
