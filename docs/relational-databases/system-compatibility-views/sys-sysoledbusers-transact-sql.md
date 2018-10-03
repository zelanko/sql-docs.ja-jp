---
title: sys.sysoledbusers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 71d04ef07053eb893a98d654424eb49b61f0c7e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809140"
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  これは、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]でシステム テーブルが含まれている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]旧バージョンとの互換性を保つのためのビューとして。 使用することをお勧めします。[カタログ ビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)代わりにします。  
  
 指定したリンク サーバーのユーザーとパスワードのマッピングごとに 1 行のデータを格納します。 **sysoledbusers**に格納されている場合は、**マスター**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|サーバーのセキュリティ識別番号 (SID)。|  
|**rmtloginame**|**nvarchar(** 128 **)**|リモート ログインの名前を**loginsid**マップのリンクされた**rmtservid**します。|  
|**rmtpassword**|**nvarchar(** 128 **)**|NULL を返します。|  
|**loginsid**|**varbinary(** 85 **)**|マップされるローカル ログインの SID。|  
|**status**|**smallint**|1 の場合、マッピングではユーザーの資格情報が使用されます。|  
|**changedate**|**datetime**|マッピング情報が前回変更された日付。|  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
