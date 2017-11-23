---
title: "sys.assembly_files (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.assembly_files
- assembly_files_TSQL
- assembly_files
- sys.assembly_files_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.assembly_files catalog view
ms.assetid: 1a384a2c-5556-4d12-a2ba-4da781363143
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dcb6fd653e2fc9811d3153e7c547c0497560684f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysassemblyfiles-transact-sql"></a>sys.assembly_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アセンブリを構成するファイルごとに 1 行のデータを保持します。  
    
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|このファイルが所属するアセンブリの ID です。|  
|**name**|**nvarchar (260)**|アセンブリ ファイルの名前です。|  
|**file_id**|**int**|ファイルの ID です。 アセンブリ内で一意です。 ファイル ID 1 は、アセンブリ DLL を表します。|  
|**コンテンツ**|**varbinary(max)**|ファイルのコンテンツです。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR アセンブリ カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
