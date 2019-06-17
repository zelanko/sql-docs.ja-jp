---
title: '[SQL Server エージェントのプロパティ] ([接続] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e6cdb4cc45876377a34e75fbdaffa8bd726d8e64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089411"
---
# <a name="sql-server-agent-properties-connection-page"></a>[SQL Server エージェントのプロパティ] ([接続] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続の設定を表示および変更できます。  
  
## <a name="options"></a>および  
**[別名ローカル ホスト サーバー]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のローカル インスタンスへの接続に使用する別名を指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの既定の接続オプションを使用できない場合は、インスタンスの別名を定義し、ここでその別名を指定します。  
  
**[Windows 認証を使用する]**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 認証を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に使用する認証方法として設定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが実行に使用するアカウントとして接続します。  
  
**[SQL Server 認証を使用する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に使用する認証方法として設定します。  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証は旧バージョンとの互換性を維持するために提供されます。 セキュリティを向上させるためには、可能な限り、Windows 認証を使用してください。  
  
**Login**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続に使用するログイン名を指定します。  
  
**Password**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続に使用するパスワードを指定します。  
  
