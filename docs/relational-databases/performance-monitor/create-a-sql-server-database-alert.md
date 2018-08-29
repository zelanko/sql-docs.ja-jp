---
title: SQL Server データベース警告の作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4b365f6e1272e413ab46035e3f093697fd7adaa8
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40410397"
---
# <a name="create-a-sql-server-database-alert"></a>SQL Server データベース警告の作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  システム モニターでは、システム モニターのカウンターがしきい値に達したときに発生する警告を作成できます。 警告が発せられると、システム モニターは、その警告状況を処理するために記述されたカスタム アプリケーションなどのアプリケーションを起動します。 たとえば、デッドロックの数が特定の値を超えたときに発生する警告を作成できます。  
  
 警告は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用して定義することもできます。 詳細については、「[警告](../../ssms/agent/alerts.md)」を参照してください。  
  
 システム モニターを使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース警告を設定する方法の詳細については、「[SQL Server データベースの警告のセットアップ &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  
