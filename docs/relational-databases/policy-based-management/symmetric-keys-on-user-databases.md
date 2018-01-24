---
title: "ユーザー データベースの対称キー | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: "6"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2eb8187d078ccd4eb60ff045bd350183080d33d6
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="symmetric-keys-on-user-databases"></a>ユーザー データベースの対称キー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このルールでは、長さが 128 バイト未満のキーが RC2 または RC4 暗号化アルゴリズムを使用していないかどうかを確認します。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 データ暗号化用の対称キーを作成する場合は、AES 128 ビット以上を使用します。 AES がオペレーティング システムでサポートされていない場合は、3DES を使用します。  
  
## <a name="for-more-information"></a>詳細情報  
 [暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
