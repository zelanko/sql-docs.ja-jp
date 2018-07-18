---
title: 包含データベースと Always On 可用性グループ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5086a557319d4db305f4a3d5d6c2df6437e3f8c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285708"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>包含データベースと Always On 可用性グループ (SQL Server)
  このトピックには、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]と共に包含データベースを使用する方法に関する情報が含まれています。  
  
 **このトピックの内容**  
  
-   [前提条件](#Prerequisites)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> 前提条件  
  
-   包含データベースを可用性グループに追加する前に、その可用性グループの可用性レプリカをホストする各サーバー インスタンスで、`contained database authentication` サーバー オプションが `1` に設定されていることを確認してください。 詳細については、「 [contained database authentication サーバー構成オプション](../../configure-windows/contained-database-authentication-server-configuration-option.md) 」および「 [サーバー構成オプション &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)と共に包含データベースを使用する方法に関する情報が含まれています。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [サーバー構成オプション &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [包含データベース](../../../relational-databases/databases/contained-databases.md)  
  
  
