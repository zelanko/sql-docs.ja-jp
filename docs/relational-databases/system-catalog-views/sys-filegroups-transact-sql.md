---
title: sys.filegroups (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.filegroups_TSQL
- filegroups
- sys.filegroups
- filegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filegroups catalog view
ms.assetid: 9e851f72-1f8e-4515-a25d-152ebc12ed56
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8a972d10b1e557793c235bf612255988a3b5de83
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ファイル グループのデータ領域ごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**|--|このビューが継承する列の一覧は、次を参照してください。 [sys.data_spaces &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)です。|  
|**filegroup_guid**|**uniqueidentifier**|ファイル グループの GUID です。<br /><br /> NULL = PRIMARY ファイル グループ|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この値は NULL です。|  
|**is_read_only**|**bit**|1 = ファイル グループは読み取り専用です。<br /><br /> 0 = ファイル グループは読み取り/書き込み可能です。|  
|**is_autogrow_all_files**|**bit**|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。<br /><br /> 1 = ファイルの自動拡張のしきい値をファイル グループ内のすべてのファイル拡張のファイル グループを満たしているときにします。<br /><br /> 0 = ファイルの自動拡張のしきい値をそのファイルのみの増加のファイル グループを満たしているときにします。 これは既定値です。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [データ領域&#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
