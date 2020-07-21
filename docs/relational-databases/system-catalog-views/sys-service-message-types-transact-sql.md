---
title: service_message_types (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 02f210ddee531fe48e7bf2861fe353b1b04ac442
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883191"
---
# <a name="sysservice_message_types-transact-sql"></a>service_message_types (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このカタログビューには、service broker に登録されているメッセージの種類ごとに1行が含まれています。
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|メッセージ型の名前。データベース内で一意です。 NULL 値は許容されません。|  
|**message_type_id**|**int**|メッセージ型の識別子。データベース内で一意です。 NULL 値は許容されません。|  
|**principal_id**|**int**|このメッセージ型を所有するデータベースプリンシパルの識別子。 NULLABLE.|  
|**検査**|**char(2)**|この型のメッセージを送信する前に、ブローカーによって実行される検証。 NULL 値は許容されません。 つぎのいずれかです。<br /><br /> N = なし<br /><br /> X = XML<br /><br /> E = 空|  
|**validation_desc**|**nvarchar(60)**|この型のメッセージを送信する前に、ブローカーで実行される検証の説明。 NULLABLE. つぎのいずれかです。<br /><br /> なし<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|XML スキーマを使用する検証の場合、使用されるスキーマ コレクションの識別子。<br /><br /> それ以外の場合は NULL。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
