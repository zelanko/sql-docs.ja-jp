---
title: パフォーマンス オブジェクトの使用 | Microsoft Docs
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
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 01d245a9ac6eb32bd38978bd2ed4189f774332ca
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982414"
---
# <a name="use-performance-objects"></a>パフォーマンス オブジェクトの使用
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> 
  [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントには、サービスの動作を監視するためのパフォーマンス オブジェクトとパフォーマンス カウンターが含まれています。 パフォーマンス オブジェクトを使用すると、パフォーマンス モニターや Windows ツールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのバックグラウンド動作を特定できるようになります。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスで現在実行されているアクティブなジョブの数を特定して、ブロックされたジョブを特定できます。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのパフォーマンス オブジェクトとパフォーマンス カウンターは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスごとに存在します。 パフォーマンス オブジェクトの名前は、各オブジェクトが表す [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスに従って付けられます。  
  
次の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのパフォーマンス オブジェクトの命名形式を示しています。  
  
|インスタンスの種類|オブジェクト名です。|  
|-----------------|---------------|  
|既定|**SQLAgent:***object*:*counter*|  
|名前付き|**SQLAgent$**<br /> **&#42;instance_name&#42; :***object*:*counter*|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの次のパフォーマンス オブジェクトが含まれています。  
  
|オブジェクト名です。|[説明]|  
|---------------|---------------|  
|[SQLAgent:Jobs](http://msdn.microsoft.com/225b5e2d-4a78-4178-b2b6-b419df83c4aa)|開始されたジョブ、成功率、および現在の状態に関するパフォーマンス情報|  
|[SQLAgent:JobSteps](http://msdn.microsoft.com/44f9983c-1753-4fe0-8475-973aa2460b3a)|ジョブ ステップに関する状態情報|  
|[SQLAgent:Alerts](http://msdn.microsoft.com/e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a)|警告と通知の数に関する情報|  
|[SQLAgent:Statistics](http://msdn.microsoft.com/ebe92bfa-0721-48aa-9ba6-e7904ad265a1)|パフォーマンスに関する一般的な情報|  
  
## <a name="see-also"></a>参照  
[パフォーマンスの監視とチューニング](http://msdn.microsoft.com/87f23f03-0f19-4b2e-bfae-efa378f7a0d4)  
[システム モニターを起動する方法 (Windows)](http://msdn.microsoft.com/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
