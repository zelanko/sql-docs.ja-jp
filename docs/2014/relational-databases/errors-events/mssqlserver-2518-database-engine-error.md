---
title: MSSQLSERVER_2518 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f40eb8fe404479f5a2bcd68881aec4b2b2d84613
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082985"
---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2518|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|メッセージ テキスト|オブジェクト ID O_ID (オブジェクト "O_NAME") : 共通言語ランタイム (CLR) が無効になっているので、このオブジェクトでは計算列とユーザー定義型を確認できません。|  
  
## <a name="explanation"></a>説明  
 この情報メッセージは、クエリ プロセッサが、計算列と共通言語ランタイム (CLR) のユーザー定義型を評価するための内部オブジェクトを DBCC に提供できなかったことを示しています。 この問題は、いずれかの列に CLR が関係しているにもかかわらず、CLR が有効化されていないために発生しました。 内部オブジェクトはすべての列に及んでいます。 このため、1 つの列を評価できないと、内部オブジェクトの作成ができなくなります。 つまり、計算列の正当性チェックが行われなかったり、DBCC でインデックスとベース テーブルの整合性をチェックする際に計算列が使用されないことを意味します。  
  
## <a name="user-action"></a>ユーザーの操作  
 CLR を有効にして、DBCC ステートメントを再実行します。  
  
## <a name="see-also"></a>参照  
 [CLR 統合の有効化](../clr-integration/clr-integration-enabling.md)  
  
  