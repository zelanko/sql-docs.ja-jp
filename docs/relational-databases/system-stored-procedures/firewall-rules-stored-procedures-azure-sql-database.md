---
title: ファイアウォール ルールのストアド プロシージャ (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/28/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- firewall rules stored procedures
- firewall_rules, setting
- firewall_rules, Azure SQL Database
- firewall systems, Azure SQL Database
ms.assetid: 3d4c2585-00de-46b5-8eee-0efb71cb3aea
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 6de7f6cc9166b63cf53b7cae71b172b43651e09e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="firewall-rules-stored-procedures-azure-sql-database"></a>ファイアウォール ルールのストアド プロシージャ (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  ここでは、ファイアウォール ルールを設定または削除する次のストアド プロシージャについて説明します。 [!INCLUDE[tsql_md](../../includes/tsql-md.md)] ファイアウォール規則で使用できる[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]と[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]です。 詳細については、次を参照してください。[ファイアウォール ルールを Azure SQL データベースの構成 - 概要](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)です。
  
 
  
|  |  |  
| - | - |  
|[sp_set_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)|[sp_delete_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)|  
|[sp_set_database_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)|[sp_delete_database_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)|  
  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ウィンドウのファイアウォール ルールを使用します。 詳しくは、「 [データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)」をご覧ください。   
  


