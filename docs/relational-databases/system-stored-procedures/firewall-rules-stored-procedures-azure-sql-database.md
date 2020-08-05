---
title: ファイアウォール ルールのストアド プロシージャ
titleSuffix: Azure SQL Database
ms.date: 07/28/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- firewall rules stored procedures
- firewall_rules, setting
- firewall_rules, Azure SQL Database
- firewall systems, Azure SQL Database
ms.assetid: 3d4c2585-00de-46b5-8eee-0efb71cb3aea
author: VanMSFT
ms.author: vanto
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: bace837ef11fc106632b84fe01ed5c8bc1448ffa
ms.sourcegitcommit: bc10ec0be5ddfc5f0bc220a9ac36c77dd6b80f1d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544352"
---
# <a name="firewall-rules-stored-procedures-azure-sql-database"></a>ファイアウォールルールのストアドプロシージャ (Azure SQL Database)
[!INCLUDE [asdb-asa](../../includes/applies-to-version/asdb-asa.md)]

  ここでは、ファイアウォール規則を設定または削除する次のストアドプロシージャについて説明します。 [!INCLUDE[tsql_md](../../includes/tsql-md.md)]ファイアウォール規則は、およびと共に使用でき [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] ます。 詳細については、「 [Azure SQL Database ファイアウォール規則の構成-概要](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)」を参照してください。

:::row:::
    :::column:::
        [sp_set_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)
    :::column-end:::
    :::column:::
        [sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [sp_set_database_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)
    :::column-end:::
    :::column:::
        [sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)
    :::column-end:::
:::row-end:::

&nbsp;
  
の場合 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] は、ウィンドウのファイアウォール規則を使用します。 詳しくは、「 [データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)」をご覧ください。   
  


