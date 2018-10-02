---
title: 予期しないシステム障害 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 050d7dbf22965cfc3b150f4ff42e3a0e437e7e8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610360"
---
# <a name="unexpected-system-failures"></a>予期しないシステム障害
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、コンピューターのイベント ログに SYSTEM イベント 6008 がないかどうかを確認します。 このイベントは、予期しないシステムのシャットダウンを示します。 システムが不安定になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをホストするために必要な安定性や整合性が提供できなくなる可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 予期しないサーバーの再起動の原因をすぐに解決するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを別のコンピューターに移動してください。  
  
  
