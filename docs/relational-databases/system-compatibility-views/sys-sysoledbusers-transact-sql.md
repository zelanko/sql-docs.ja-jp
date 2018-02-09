---
title: "sys.sysoledbusers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97cad6b87bbcad6bbc551ce675cf0c84850e7f3d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  これは、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]システム テーブルに格納されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]旧バージョンとの互換性を保つのためのビューとして。 使用することをお勧め[カタログ ビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)代わりにします。  
  
 指定したリンク サーバーのユーザーとパスワードのマッピングごとに 1 行のデータを格納します。 **sysoledbusers**に格納されて、**マスター**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|サーバーのセキュリティ識別番号 (SID)。|  
|**rmtloginame**|**nvarchar(**128**)**|リモート ログインの名前を**loginsid**リンク用にマップ**rmtservid**です。|  
|**rmtpassword**|**nvarchar(**128**)**|Returns NULL.|  
|**loginsid**|**varbinary(**85**)**|マップされるローカル ログインの SID。|  
|**ステータス**|**smallint**|1 の場合、マッピングではユーザーの資格情報が使用されます。|  
|**changedate**|**datetime**|マッピング情報が前回変更された日付。|  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
