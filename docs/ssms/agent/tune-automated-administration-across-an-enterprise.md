---
title: 企業全体の自動管理のチューニング
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b43a1298c16ba1e51459852f8c775dd67b5b4a7b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755031"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>企業全体の自動管理のチューニング

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによるマルチサーバー管理では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の自己チューニング機能を活用しています。 したがって、通常の条件下では、新たにジョブのチューニングを行う必要はありません。 ただし、ジョブの実行、警告の生成、オペレーターへの通知などを行うと、ネットワークの負荷が増加します。 これらの動作によって生じるネットワーク トラフィックを最小限に抑えるために、企業全体の自動管理をチューニングできます。  

## <a name="see-also"></a>参照

[データ フロー エンジンのパフォーマンスの監視](../../integration-services/performance/performance-counters.md)