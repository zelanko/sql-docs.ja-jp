---
title: トランザクションの有効期間 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 46de36a86103e5f6d9d9c652b17aba3f8602e1c1
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353584"
---
# <a name="transaction-lifetimes"></a>トランザクションの有効期間
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ph x="1" /&gt; ストアド プロシージャで開始されるトランザクションとマネージド コードで開始されるトランザクションには重要な違いがあります。CLR (共通言語ランタイム) コードでは、CLR 呼び出しの開始時または終了時にトランザクションの状態を不安定にすることはできません。 この違いにより、次の点に注意してください。  
  
-   CLR フレーム内部で開始されたトランザクションは、そのフレーム内でコミットまたはロールバックする必要があります。コミットまたはロールバックしなかった場合、そのフレームの終了時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によりエラーが生成されます。  
  
-   CLR コード内部から外部のトランザクションをコミットまたはロールバックすることはできません。  
  
-   同じプロシージャ内で開始されていないトランザクションをコミットしようとすると、実行時エラーが発生します。  
  
-   同じプロシージャ内で開始されていないトランザクションをロールバックしようとすると、そのトランザクションが応答を停止します (ロールバックに伴う他の二次的な動作が行われません)。 トランザクションは、CLR コードがスコープ外になるまで再開されません。 この動作は、プロシージャ内部でエラーを検出したときに、トランザクション全体を終了することが望ましい場合に役立つことがあります。  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
