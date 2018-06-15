---
title: '[SQL Server エージェント エラー ログの再利用] | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e1845c8b775debcd15a195826ec4a2912fbf1bd2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33040799"
---
# <a name="recycle-sql-server-agent-error-logs"></a>[SQL Server エージェント エラー ログの再利用]
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント エラー ログを再利用できます。 ログを再利用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを再起動しなくても、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント エラー ログが閉じ、新しいエラー ログが開始します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントで保持されるエラー ログは直前の 9 個までであることに注意してください。 既にエラー ログが 9 個に達している場合は、エラー ログを再利用すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは最も古いエラーログを削除します。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェント エラー ログ](../../ssms/agent/sql-server-agent-error-log.md)  
  
