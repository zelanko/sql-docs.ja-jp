---
title: '[プロキシ アカウントのプロパティ] - [新しいプロキシ アカウント]\([全般] ページ) | Microsoft Docs'
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
- sql13.ag.proxy.general.f1
ms.assetid: 5cd81265-bf59-413b-8397-150ddc70d0c7
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f0d7a1ce8d98c6817b831cf858a2012cf9736169
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000264"
---
# <a name="proxy-account-properties---new-proxy-account-general-page"></a>[プロキシ アカウントのプロパティ] - [新しいプロキシ アカウント]\([全般] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント プロキシ アカウントのプロパティを表示したり変更したりできます。  
  
## <a name="options"></a>および  
**[プロキシ名]**  
プロキシの名前を入力します。  
  
**[資格情報名]**  
プロキシの資格情報の名前を入力します。  
  
> [!NOTE]  
> 指定する資格情報名は、既存の資格情報の名前である必要があります。 資格情報を作成する方法の詳細については、「 [プロキシを作成する方法 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/c1e77e91-2a69-40d9-b8b3-97cffc710586)」を参照してください。  
  
**[...]**  
**[資格情報の選択]** ダイアログを起動します。  
  
**[説明]**  
プロキシの説明を入力します。  
  
**[以下のサブシステムに対してアクティブ]**  
プロキシ アカウントがアクセスできるサブシステムを選択します。  
  
**[以下にジョブ ステップを再度割り当てます]**  
ジョブ ステップを再度割り当てるプロキシを選択します。 プロキシが以前アクセスしていたサブシステムに対するアクセスを取り消すときに、この一覧が使用できるようになります。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェント プロキシの作成](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
