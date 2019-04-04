---
title: sys.filegroups (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 479ba4e8eefadfe37cccb1ff08aed38ab8b629a7
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666378"
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ファイル グループのデータ領域ごとに 1 行のデータを保持します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<列を継承 >**|--|このビューが継承する列の一覧は、[sys.data_spaces &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)を参照してください。|  
|**filegroup_guid**|**uniqueidentifier**|ファイル グループの GUID です。<br /><br /> NULL = PRIMARY ファイル グループ|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この値は NULL です。|  
|**is_read_only**|**bit**|1 = ファイル グループは読み取り専用です。<br /><br /> 0 = ファイル グループは読み取り/書き込み可能です。|  
|**is_autogrow_all_files**|**bit**|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](https://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。<br /><br /> 1 = ファイルで自動拡張のしきい値をファイル グループ内のすべてのファイルの拡張ファイル グループを満たしている場合。<br /><br /> 0 = 自動拡張のしきい値、そのファイルのみの増加を満たしているファイル グループ内のファイルの場合。 既定値です。|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [データ領域&#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
