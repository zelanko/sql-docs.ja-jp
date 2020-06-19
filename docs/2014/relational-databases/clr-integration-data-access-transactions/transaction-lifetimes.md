---
title: トランザクションの有効期間 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c00050ee323cade7493d44c4c296ba4ce6811e0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84955132"
---
# <a name="transaction-lifetimes"></a>トランザクションの有効期間
  [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで開始されるトランザクションとマネージド コードで開始されるトランザクションには重要な違いがあります。CLR (共通言語ランタイム) コードでは、CLR 呼び出しの開始時または終了時にトランザクションの状態を不安定にすることはできません。 この違いにより、次の点に注意してください。  
  
-   CLR フレーム内部で開始されたトランザクションは、そのフレーム内でコミットまたはロールバックする必要があります。コミットまたはロールバックしなかった場合、そのフレームの終了時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によりエラーが生成されます。  
  
-   CLR コード内部から外部のトランザクションをコミットまたはロールバックすることはできません。  
  
-   同じプロシージャ内で開始されていないトランザクションをコミットしようとすると、実行時エラーが発生します。  
  
-   同じプロシージャ内で開始されていないトランザクションをロールバックしようとすると、トランザクションが応答を停止します (他の副作用操作が発生するのを防ぐことができます)。 トランザクションは、CLR コードがスコープ外になるまで再開されません。 この動作は、プロシージャ内部でエラーを検出したときに、トランザクション全体を終了することが望ましい場合に役立つことがあります。  
  
## <a name="see-also"></a>参照  
 [CLR 統合とトランザクション](../native-client-ole-db-transactions/transactions.md)  
  
  
