---
title: 包含データベースと Always On 可用性グループ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c8a0b41ee7224dad83fb41691a4898c15b7b38
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936915"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>包含データベースと Always On 可用性グループ (SQL Server)
  このトピックには、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]と共に包含データベースを使用する方法に関する情報が含まれています。  
  
 **このトピックの内容**  
  
-   [前提条件](#Prerequisites)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> 必要条件  
  
-   包含データベースを可用性グループに追加する前に、その可用性グループの可用性レプリカをホストする各サーバー インスタンスで、`contained database authentication` サーバー オプションが `1` に設定されていることを確認してください。 詳細については、「 [contained database authentication サーバー構成オプション](../../configure-windows/contained-database-authentication-server-configuration-option.md) 」および「 [サーバー構成オプション &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)と共に包含データベースを使用する方法に関する情報が含まれています。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [サーバー構成オプション &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [包含データベース](../../../relational-databases/databases/contained-databases.md)  
  
  
