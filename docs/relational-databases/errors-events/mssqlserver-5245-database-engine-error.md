---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 25109bc21ea0ec035aa30e7ba439dcd967c4ac55
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver5245"></a>MSSQLSERVER_5245
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5245|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|メッセージ テキスト|オブジェクト ID O_ID (オブジェクト 'NAME'): DBCC ではこのオブジェクトをロックできませんでした。ロック要求がタイムアウトしました。 このオブジェクトはスキップされたので、処理されません。|  
  
## <a name="explanation"></a>説明  
DBCC が、指定されたオブジェクト用にテーブルのロック獲得を待機している間に、ロック要求のタイムアウトが発生しました。  
  
## <a name="user-action"></a>ユーザーの操作  
DBCC コマンドを再実行します。  
  

