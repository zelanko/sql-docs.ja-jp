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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb25dc5548378c8057c7f3f90168bab5d85c8e7b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="symmetric-keys-on-user-databases"></a>ユーザー データベースの対称キー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このルールでは、長さが 128 バイト未満のキーが RC2 または RC4 暗号化アルゴリズムを使用していないかどうかを確認します。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 データ暗号化用の対称キーを作成する場合は、AES 128 ビット以上を使用します。 AES がオペレーティング システムでサポートされていない場合は、3DES を使用します。  
  
## <a name="for-more-information"></a>詳細情報  
 [暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
