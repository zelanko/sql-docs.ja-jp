---
title: "可用性データベースのデータ同期状態が正常でない | Microsoft Docs"
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
  - "sql13.swb.agdashboard.arp3datasynchealthy.issues.f1"
helpviewer_keywords: 
  - "可用性グループ [SQL Server]、ポリシー"
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "erikre"
caps.handback.revision: 15
---
# 可用性データベースのデータ同期状態が正常でない
    
## 概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性データベースのデータ同期状態|  
|**問題点**|可用性データベースのデータ同期状態が正常ではありません。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性データベース|  
  
## 説明  
 このポリシーは、可用性レプリカ内のすべての可用性データベース ("データベース レプリカ" とも呼ばれます) のデータ同期状態を集計します。 いずれかのデータベース レプリカが予想されるデータ同期状態ではない場合、ポリシーは通常とは異なる状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のこのリリース向けに、TechNet Wiki の「[一部の可用性データベースのデータ同期状態が正常でない](http://go.microsoft.com/fwlink/p/?LinkId=220858)」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## 考えられる原因  
 この可用性データベースのデータ同期状態が正常ではありません。 非同期コミット可用性レプリカでは、各可用性データベースは SYNCHRONIZING 状態である必要があります。 同期コミット レプリカでは、各可用性データベースは SYNCHRONIZED 状態である必要があります。  
  
## 考えられる解決方法  
 データベース レプリカ ポリシーを使用して通常とは異なるデータ同期状態のデータベース レプリカを見つけ、データベース レプリカの問題を解決します。  
  
## 参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../Topic/Overview%20of%20Always On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  