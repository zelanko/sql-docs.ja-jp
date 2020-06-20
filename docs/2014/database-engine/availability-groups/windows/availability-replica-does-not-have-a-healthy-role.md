---
title: 正常なロールのない可用性レプリカ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48dc4150c79225e069ea4e340e82458b42b4be6d
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937083"
---
# <a name="availability-replica-does-not-have-a-healthy-role"></a>正常なロールのない可用性レプリカ
    
## <a name="introduction"></a>はじめに  
  
|||  
|-|-|  
|**[ポリシー名]**|可用性レプリカのロールの状態|  
|**問題点**|可用性レプリカに正常なロールがありません。|  
|**カテゴリ**|**重大**|  
|**面し**|可用性レプリカ|  
  
## <a name="description"></a>説明  
 このポリシーは、可用性レプリカのロールの状態をチェックします。 可用性レプリカのロールがプライマリでもセカンダリでもない場合、ポリシーは異常な状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性レプリカに正常なロールがない](https://go.microsoft.com/fwlink/p/?LinkId=220856) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 この可用性レプリカのロールが正常ではありません。 このレプリカにはプライマリ ロールもセカンダリ ロールも割り当てられていません。  
  
## <a name="possible-solution-information_still_to_come"></a>考えられる解決方法: ここに情報を挿入  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
