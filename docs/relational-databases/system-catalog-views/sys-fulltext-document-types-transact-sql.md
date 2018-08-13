---
title: sys.fulltext_document_types (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fulltext_document_types_TSQL
- fulltext_document_types
- fulltext_document_types_TSQL
- sys.fulltext_document_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_document_types catalog view
ms.assetid: 156fcfa4-7304-4a5c-b96f-1c3e061e5df0
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 2893dd860fc60714538e8365939a13153c62f6a4
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39543502"
---
# <a name="sysfulltextdocumenttypes-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト インデックス操作に使用できるドキュメント型ごとに 1 行のデータを返します。 インスタンスに登録されている IFilter インターフェイスが各行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|サポートされているドキュメント型のファイル拡張子。<br /><br /> この値は、型の列のフルテキスト インデックスの作成中に使用されるフィルターを識別するために使用できます**varbinary (max)** または**イメージ**します。|  
|**class_id**|**uniqueidentifier**|ファイル拡張子をサポートする IFilter クラスの GUID。|  
|**path**|**nvarchar(260)**|IFilter DLL へのパス。 パスが表示のメンバーにのみ、 **serveradmin**固定サーバー ロール。|  
|**version**|**sysname**|IFilter DLL のバージョン。|  
|**manufacturer**|**sysname**|IFilter 製造元の名前。<br /><br /> 注: として、製造元のドキュメントのみ[!INCLUDE[msCoName](../../includes/msconame-md.md)]ではサポートされている[!INCLUDE[ssSDS](../../includes/sssds-md.md)]。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
