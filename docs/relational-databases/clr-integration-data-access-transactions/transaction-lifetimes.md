---
title: トランザクションの有効期間 |マイクロソフトドキュメント
description: SQL Server CLR 統合でのトランザクションの有効期間について説明します。 Transact-SQL ストアド プロシージャで開始されるトランザクションは、マネージ コードで開始されるトランザクションとは異なります。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 1fed737c644ebb241a5761fffd2409c2556d28ea
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487510"
---
# <a name="transaction-lifetimes"></a>トランザクションの有効期間
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで開始されるトランザクションとマネージド コードで開始されるトランザクションには重要な違いがあります。CLR (共通言語ランタイム) コードでは、CLR 呼び出しの開始時または終了時にトランザクションの状態を不安定にすることはできません。 この違いにより、次の点に注意してください。  
  
-   CLR フレーム内部で開始されたトランザクションは、そのフレーム内でコミットまたはロールバックする必要があります。コミットまたはロールバックしなかった場合、そのフレームの終了時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によりエラーが生成されます。  
  
-   CLR コード内部から外部のトランザクションをコミットまたはロールバックすることはできません。  
  
-   同じプロシージャ内で開始されていないトランザクションをコミットしようとすると、実行時エラーが発生します。  
  
-   同じ手順で開始されていないトランザクションをロールバックしようとすると、トランザクションが応答を停止します (他の副作用操作が発生しないようにします)。 トランザクションは、CLR コードがスコープ外になるまで再開されません。 この動作は、プロシージャ内部でエラーを検出したときに、トランザクション全体を終了することが望ましい場合に役立つことがあります。  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
