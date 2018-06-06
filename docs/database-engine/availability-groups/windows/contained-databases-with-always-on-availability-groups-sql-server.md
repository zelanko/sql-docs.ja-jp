---
title: 包含データベースと Always On 可用性グループ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8226893f960bd0c1b64c589219121f323226766d
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768648"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>包含データベースと Always On 可用性グループ (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックには、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]と共に包含データベースを使用する方法に関する情報が含まれています。  
  
 **このトピックの内容**  
  
-   [前提条件](#Prerequisites)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> 前提条件  
  
-   包含データベースを可用性グループに追加する前に、その可用性グループの可用性レプリカをホストする各サーバー インスタンスで、 **contained database authentication** のサーバー オプションが **1** に設定されていることを確認してください。 詳細については、「 [contained database authentication サーバー構成オプション](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) 」および「 [サーバー構成オプション &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)と共に包含データベースを使用する方法に関する情報が含まれています。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [サーバー構成オプション &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [包含データベース](../../../relational-databases/databases/contained-databases.md)  
  
  
