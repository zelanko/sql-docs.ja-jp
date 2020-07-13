---
title: 可用性レプリカが参加していない | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp4joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab8f136a021d973b7c9653ea0ba9c4b1875c1402
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937039"
---
# <a name="availability-replica-is-not-joined"></a>可用性レプリカが参加していない
    
## <a name="introduction"></a>はじめに  
  
|||  
|-|-|  
|**[ポリシー名]**|可用性レプリカの参加状態|  
|**問題点**|可用性レプリカが参加していません。|  
|**カテゴリ**|**警告**|  
|**面し**|可用性レプリカ|  
  
## <a name="description"></a>説明  
 このポリシーは、可用性レプリカの参加状態をチェックします。 可用性レプリカが可用性グループに追加されていても、適切に参加していない場合、ポリシーは異常な状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Availability Replica Is not joined (可用性レプリカが参加していない)](https://go.microsoft.com/fwlink/p/?LinkId=220859) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 セカンダリ レプリカが可用性グループに参加していません。 可用性レプリカを可用性グループに正しく参加させるには、参加状態が Joined Standalone Instance (1) または Joined Failover Cluster (2) である必要があります。  
  
## <a name="possible-solution"></a>考えられる解決方法  
 Transact-SQL、PowerShell、または SQL Server Management Studio を使用して、セカンダリ レプリカを可用性グループに参加させます。 セカンダリ レプリカを可用性グループに参加させる方法の詳細については、「 [可用性グループへのセカンダリ レプリカの参加 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
