---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: eafae8fdc25989aaec7ea987d5e72ed7a9221e93
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver5237"></a>MSSQLSERVER_5237
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5237|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|メッセージ テキスト|オブジェクト 'NAME' (オブジェクト ID O_ID) で、内部クエリ エラーにより、DBCC クロス行セットのチェックに失敗しました。|  
  
## <a name="explanation"></a>説明  
内部エラーが発生したため、DBCC は、クエリを実行してインデックス付きビューをチェックすることができませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
DBCC コマンドを再実行します。  
  
