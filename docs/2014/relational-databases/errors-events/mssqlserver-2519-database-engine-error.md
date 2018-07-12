---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3262e6bbb1c78bc7c4f504cd9d102687c16b6afa
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431791"
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2519|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_NO_EXPRESSION_EVALUATOR|  
|メッセージ テキスト|内部の式エバリュエーターを初期化できなかったため、オブジェクト ID O_ID (オブジェクト "O_NAME") の計算列とユーザー定義型を確認できません。|  
  
## <a name="explanation"></a>説明  
 この情報メッセージは、クエリ プロセッサが、計算列と CLR (common language runtime) ユーザー定義型を評価するための内部オブジェクトを DBCC に提供できなかったことを示しています。 つまり、計算列および CLR ユーザー定義型の正当性チェックが行われなかったり、DBCC でインデックスとベース テーブルの整合性をチェックする際に計算列が使用されないことを意味します。  
  
## <a name="user-action"></a>ユーザーの操作  
 なし  
  
## <a name="see-also"></a>参照  
 [MSSQLSERVER_2518](mssqlserver-2518-database-engine-error.md)  
  
  
