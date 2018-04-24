---
title: 予期しないシステム障害 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a01dbd774aaaecb7b00baff624dc65c003e6cdd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="unexpected-system-failures"></a>予期しないシステム障害
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、コンピューターのイベント ログに SYSTEM イベント 6008 がないかどうかを確認します。 このイベントは、予期しないシステムのシャットダウンを示します。 システムが不安定になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをホストするために必要な安定性や整合性が提供できなくなる可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 予期しないサーバーの再起動の原因をすぐに解決するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを別のコンピューターに移動してください。  
  
  
