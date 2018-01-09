---
title: "CLR ユーザー定義集計 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33746938a6121e0caaa94f2f71c84f400d5faace
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="clr-user-defined-aggregates"></a>CLR ユーザー定義集計
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]集計関数は、一連の値に対して計算を実行し、1 つの値を返します。 従来、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、サポートされる組み込み集計関数のみをなど**合計**または**MAX**一連の入力スカラー値に対して機能し、1 つの集計を生成します。そのセットからの値。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (共通言語ランタイム) と統合されたことにより、開発者はマネージ コードでカスタム集計関数を作成し、[!INCLUDE[tsql](../../includes/tsql-md.md)] や他のマネージ コードから作成した関数にアクセスできるようになりました。  
  
 次の表は、このセクションのトピックを一覧表示します。  
  
 [CLR ユーザー定義集計の要件](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 CLR ユーザー定義集計関数の実装要件の概要について説明します。  
  
 [CLR ユーザー定義集計関数の呼び出し](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 ユーザー定義集計を呼び出す方法について説明します。  
  
  
