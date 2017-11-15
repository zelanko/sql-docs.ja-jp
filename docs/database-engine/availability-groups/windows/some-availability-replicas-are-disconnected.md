---
title: "いくつかの可用性レプリカが切断されている | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords: Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1dae927419403deb993127620c3ff7a012241b7b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="some-availability-replicas-are-disconnected"></a>いくつかの可用性レプリカが切断されている
    
## <a name="introduction"></a>概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性レプリカの接続状態|  
|**問題点**|一部の可用性レプリカの接続が解除されます。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性グループ|  
  
## <a name="description"></a>説明  
 このポリシーは、すべての可用性レプリカの接続状態をロール アップし、DISCONENCTED 状態の可用性レプリカがないか確認します。 DISCONNECTED の可用性レプリカが存在する場合、ポリシーは異常な状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Some availability replicas are disconnected (いくつかの可用性レプリカが切断されている)](http://go.microsoft.com/fwlink/p/?LinkId=220855) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 プライマリ レプリカに接続されていないセカンダリ レプリカがこの可用性グループに少なくとも 1 つ存在します。 接続状態は DISCONNECTED です。  
  
## <a name="possible-solution"></a>考えられる解決方法  
 可用性レプリカのポリシーの状態を検索条件として、DISCONNECTED 状態の可用性レプリカを探し、問題を解決してください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
