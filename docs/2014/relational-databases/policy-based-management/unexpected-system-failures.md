---
title: 予期しないシステム障害 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 951b49c0356ae27cb58041af5186becfd12853bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62677061"
---
# <a name="unexpected-system-failures"></a>予期しないシステム障害
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、コンピューターのイベント ログに SYSTEM イベント 6008 がないかどうかを確認します。 このイベントは、予期しないシステムのシャットダウンを示します。 システムが不安定になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをホストするために必要な安定性や整合性が提供できなくなる可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 予期しないサーバーの再起動の原因をすぐに解決するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを別のコンピューターに移動してください。  
  
  
