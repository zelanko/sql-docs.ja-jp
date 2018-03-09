---
title: "sys.fulltext_document_types (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26a1729aac9094d0b0f150d64772229d7f89c20a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysfulltextdocumenttypes-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト インデックス操作に使用できるドキュメント型ごとに 1 行のデータを返します。 インスタンスに登録されている IFilter インターフェイスが各行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|サポートされているドキュメント型のファイル拡張子。<br /><br /> この値は、型の列のフルテキスト インデックスの作成中に使用されるフィルターを特定する使用できる**varbinary (max)**または**イメージ**です。|  
|**class_id**|**uniqueidentifier**|ファイル拡張子をサポートする IFilter クラスの GUID。|  
|**path**|**nvarchar(260)**|IFilter DLL へのパス。 パスが表示のメンバーにのみ、 **serveradmin**固定サーバー ロール。|  
|**version**|**sysname**|IFilter DLL のバージョン。|  
|**manufacturer**|**sysname**|IFilter 製造元の名前。<br /><br /> 注: として、製造元のドキュメントのみ[!INCLUDE[msCoName](../../includes/msconame-md.md)]ではサポートされている[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
