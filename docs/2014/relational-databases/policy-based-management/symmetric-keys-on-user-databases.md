---
title: ユーザー データベースの対称キー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8f8a87976d4db4e00207822bbd171e2fb0844dcb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284948"
---
# <a name="symmetric-keys-on-user-databases"></a>ユーザー データベースの対称キー
  このルールでは、長さが 128 バイト未満のキーが RC2 または RC4 暗号化アルゴリズムを使用していないかどうかを確認します。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 データ暗号化用の対称キーを作成する場合は、AES 128 ビット以上を使用します。 AES がオペレーティング システムでサポートされていない場合は、3DES を使用します。  
  
## <a name="for-more-information"></a>詳細情報  
 [暗号化アルゴリズムの選択](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
