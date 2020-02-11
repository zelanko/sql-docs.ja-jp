---
title: 予期しないシステム障害 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 951b49c0356ae27cb58041af5186becfd12853bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62677061"
---
# <a name="unexpected-system-failures"></a>予期しないシステム障害
  このルールでは、コンピューターのイベント ログに SYSTEM イベント 6008 がないかどうかを確認します。 このイベントは、予期しないシステムのシャットダウンを示します。 システムが不安定になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをホストするために必要な安定性や整合性が提供できなくなる可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 予期しないサーバーの再起動の原因をすぐに解決するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを別のコンピューターに移動してください。  
  
  
