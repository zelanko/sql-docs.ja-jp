---
title: ネットワーク パケット サイズは 8060 バイトを超えることはできない | Microsoft Docs
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
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b7af9200587423dd8229ce699ed036cc4ce24f1f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303682"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>ネットワーク パケット サイズは 8060 バイトを超えることはできない
  sp_configure の 'network packet size' に指定された値またはログイン ユーザーのネットワーク パケット サイズが 8060 バイトを超えている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、異なるメモリ割り当て操作が実行されます。 これにより、バッファー プールに予約されていない、プロセスの仮想アドレス空間が増加する可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 ネットワーク パケット サイズが 8060 バイトを超えないようにする必要があります。  
  
## <a name="for-more-information"></a>詳細情報  
 [サポート技術情報の資料 903002](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
