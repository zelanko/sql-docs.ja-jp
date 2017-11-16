---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2877d4021c636fdefb0b71ed4ae99cf6c2cd44e5
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver8621"></a>MSSQLSERVER_8621
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8621|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|OPTIMIZER_STACK_OVERFLOW_ERR|  
|メッセージ テキスト|クエリ プロセッサはクエリ最適化実行中にスタック領域不足になりました。 クエリを簡単にしてください。|  
  
## <a name="explanation"></a>説明  
このエラーの原因として最も多いのは、クエリのサイズが大きくなったことです。 大きくなったクエリでは、各ビューの定義、計算列、[!INCLUDE[tsql](../../includes/tsql-md.md)] 関数、参照している共通テーブル式や、セカンダリ インデックス、ビュー、およびトリガーの更新などの連鎖動作が、元のクエリに置き換わっています。  
  
ビュー定義で参照しているテーブルの数や、非常に大きなスカラー式など、特定の項目によりクエリのサイズが大きくなっていることが考えられます。  
  
## <a name="user-action"></a>ユーザーの操作  
最も大きい項目に関してクエリを複数に分割することにより、クエリを単純化します。 まず不要なクエリ要素を削除し、次に一時テーブルを追加して、クエリを 2 つに分割します。  クエリの一部をサブクエリまたは関数や共通テーブルに移動するだけでは、十分ではありません。これらは [!INCLUDE[tsql](../../includes/tsql-md.md)] コンパイラを実行すると結合されるからです。  
  

