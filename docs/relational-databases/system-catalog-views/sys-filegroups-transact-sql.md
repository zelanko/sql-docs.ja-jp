---
title: sys. ファイルグループ (Transact-sql) |Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 313c0b80a1bf1d2a094760198053e26426e99c36
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68005175"
---
# <a name="sysfilegroups-transact-sql"></a>sys. ファイルグループ (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ファイルグループであるデータ領域ごとに1行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<継承された列>**|--|このビューが継承する列の一覧については、「 [sys. data_spaces &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)」を参照してください。|  
|**filegroup_guid**|**uniqueidentifier**|ファイルグループの GUID。<br /><br /> NULL = プライマリファイルグループ|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この値は NULL です。|  
|**is_read_only**|**bit**|1 = ファイルグループは読み取り専用です。<br /><br /> 0 = ファイル グループは読み取り/書き込み可能です。|  
|**is_autogrow_all_files**|**bit**|**に適用さ**れます: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](https://go.microsoft.com/fwlink/p/?LinkId=299658))。<br /><br /> 1 = ファイルグループ内のファイルが自動拡張のしきい値を満たしている場合、ファイルグループ内のすべてのファイルが拡張されます。<br /><br /> 0 = ファイルグループ内のファイルが自動拡張のしきい値を満たしている場合、そのファイルだけが拡張されます。 既定値です。|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [データ領域 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
