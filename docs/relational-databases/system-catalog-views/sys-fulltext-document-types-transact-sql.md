---
title: fulltext_document_types (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e60f977c220d14680499ca12a4884e912587b7b6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68133851"
---
# <a name="sysfulltext_document_types-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキストインデックス作成操作で使用できるドキュメントの種類ごとに1行の値を返します。 各行は、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに登録されている IFilter インターフェイスを表します。  
  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|サポートされているドキュメントの種類のファイル拡張子。<br /><br /> この値は、 **varbinary (max)** 型または**image**型の列のフルテキストインデックス作成時に使用されるフィルターを識別するために使用できます。|  
|**class_id**|**uniqueidentifier**|ファイル拡張子をサポートする IFilter クラスの GUID。|  
|**path**|**nvarchar(260)**|IFilter DLL へのパス。 このパスは、 **serveradmin**固定サーバーロールのメンバーだけに表示されます。|  
|**version**|**sysname**|IFilter DLL のバージョン。|  
|**manufacturer**|**sysname**|IFilter 製造元の名前。<br /><br /> 注: で[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDS](../../includes/sssds-md.md)]サポートされているのは製造元のドキュメントのみです。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
