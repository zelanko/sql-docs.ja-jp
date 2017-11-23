---
title: "sys.server_triggers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_triggers
- sys.server_triggers_TSQL
- server_triggers_TSQL
- sys.server_triggers
dev_langs: TSQL
helpviewer_keywords: sys.server_triggers catalog view
ms.assetid: 25926ff4-9271-45bf-bc32-d5d3344bd47a
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 15dd37e207117020fb1771e5ebf746db8a2cc145
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysservertriggers-transact-sql"></a>sys.server_triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  TR または TA の object_type を持つすべてのサーバーレベル DDL トリガーのセットを含みます。 CLR トリガーの場合は、アセンブリに読み込まれたにする必要があります、**マスター**データベース。 すべてのサーバーレベル DDL トリガー名は、単一のグローバル スコープ内に存在します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|トリガーの名前。|  
|**object_id**|**int**|オブジェクトの ID。|  
|**parent_class**|**tinyint**|親のクラスです。 常に次の値をとります。<br /><br /> 100 = サーバー|  
|**parent_class_desc**|**nvarchar (60)**|親のクラスの説明です。 常に次の値をとります。<br /><br /> サーバー。|  
|**parent_id**|**int**|SERVER 上のトリガーに対しては常に 0 です。|  
|**型**|**char(2)**|オブジェクトの種類:<br /><br /> TA = アセンブリ (CLR) トリガー<br /><br /> TR = SQL トリガー|  
|**type_desc**|**nvarchar (60)**|オブジェクトの種類のクラスの説明です。<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|トリガーが作成された日付。|  
|**modify_date**|**datetime**|トリガーが ALTER ステートメントを使用して最後に変更された日付です。|  
|**is_ms_shipped**|**bit**|内部で、ユーザーの代理として作成されたトリガー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントです。|  
|**is_disabled**|**bit**|1 = トリガーが無効です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
