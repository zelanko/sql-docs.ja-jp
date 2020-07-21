---
title: 可用性データベースのデータ同期状態が正常でない | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ed541e86bf531dd9681e9926e4acb6d1bdc6042
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936870"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>可用性データベースのデータ同期状態が正常でない
    
## <a name="introduction"></a>はじめに  
  
|||  
|-|-|  
|**[ポリシー名]**|可用性データベースのデータ同期状態|  
|**問題点**|可用性データベースのデータ同期状態が正常ではありません。|  
|**カテゴリ**|**警告**|  
|**面し**|可用性データベース|  
  
## <a name="description"></a>説明  
 このポリシーは、可用性レプリカ内のすべての可用性データベース ("データベース レプリカ" とも呼ばれます) のデータ同期状態を集計します。 いずれかのデータベース レプリカが予想されるデータ同期状態ではない場合、ポリシーは通常とは異なる状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [一部の可用性データベースのデータ同期状態が正常でない](https://go.microsoft.com/fwlink/p/?LinkId=220858) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 この可用性データベースのデータ同期状態が正常ではありません。 非同期コミット可用性レプリカでは、各可用性データベースは SYNCHRONIZING 状態である必要があります。 同期コミット レプリカでは、各可用性データベースは SYNCHRONIZED 状態である必要があります。  
  
## <a name="possible-solution"></a>考えられる解決方法  
 データベース レプリカ ポリシーを使用して通常とは異なるデータ同期状態のデータベース レプリカを見つけ、データベース レプリカの問題を解決します。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
