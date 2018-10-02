---
title: アップグレード後のプラン ガイドの検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 43c7297f490c913663c8d08f62cabb7a21cca86d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636949"
---
# <a name="validate-plan-guides-after-upgrade"></a>アップグレード後のプラン ガイドの検証
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  アプリケーションを新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のリリースにアップグレードした場合は、プラン ガイドの定義を再評価し、テストすることをお勧めします。 新しいリリースでは、パフォーマンス チューニングの要件とプラン ガイドの照合動作が異なる場合があります。 無効なプラン ガイドが原因でクエリが失敗することはありませんが、そのプラン ガイドは使用されずにプランがコンパイルされるので、最適な選択ではない場合があります。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にデータベースをアップグレードした後は、次の作業を実行することをお勧めします。  
  
-   既存のプラン ガイドを [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) 関数を使用して検証する。  
  
-   拡張イベントで、プラン ガイドによって不適切に生成されたプランがないか、 [Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) イベントを使用して一定期間の間監視する。  
  
  
