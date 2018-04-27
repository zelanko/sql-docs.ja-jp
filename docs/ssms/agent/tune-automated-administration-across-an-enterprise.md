---
title: 企業全体の自動管理のチューニング | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 952fe37adc74e5ba7312e2ba1afd40ff50f74249
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="tune-automated-administration-across-an-enterprise"></a>企業全体の自動管理のチューニング
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによるマルチサーバー管理では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の自己チューニング機能を活用しています。 したがって、通常の条件下では、新たにジョブのチューニングを行う必要はありません。 ただし、ジョブの実行、警告の生成、オペレーターへの通知などを行うと、ネットワークの負荷が増加します。 これらの動作によって生じるネットワーク トラフィックを最小限に抑えるために、企業全体の自動管理をチューニングできます。  
  
## <a name="see-also"></a>参照  
[データ フロー エンジンのパフォーマンスの監視](http://msdn.microsoft.com/en-us/11e17f4e-72ed-44d7-a71d-a68937a78e4c)  
  
