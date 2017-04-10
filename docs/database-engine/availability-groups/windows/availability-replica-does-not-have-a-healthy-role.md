---
title: "正常なロールのない可用性レプリカ | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.arp1rolehealthy.issues.f1"
helpviewer_keywords: 
  - "可用性グループ [SQL Server]、ポリシー"
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
caps.latest.revision: 13
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 13
---
# 正常なロールのない可用性レプリカ
    
## 概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性レプリカのロールの状態|  
|**問題点**|可用性レプリカに正常なロールがありません。|  
|**カテゴリ**|**重大**|  
|**ファセット**|可用性レプリカ|  
  
## 説明  
 このポリシーは、可用性レプリカのロールの状態をチェックします。 可用性レプリカのロールがプライマリでもセカンダリでもない場合、ポリシーは異常な状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のこのリリース向けに、TechNet Wiki の「[可用性レプリカに正常なロールがない](http://go.microsoft.com/fwlink/p/?LinkId=220856)」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## 考えられる原因  
 この可用性レプリカのロールが正常ではありません。 このレプリカにはプライマリ ロールもセカンダリ ロールも割り当てられていません。  
  
## 考えられる解決方法: ここに情報を挿入  
  
## 参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Always On ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  