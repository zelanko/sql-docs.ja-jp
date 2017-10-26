---
title: MSSQLSERVER_4064 | Microsoft Docs
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
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ff8f948a1c94fcfcb36f43d0644e251e027a02c5
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|4064|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DB_UFAIL_FATAL|  
|メッセージ テキスト|ユーザーの既定データベースを開けません。 ログインできませんでした。|  
  
## <a name="explanation"></a>説明  
SQL Server ログインの既定のデータベースに問題があるため接続できませんでした。 データベース自体が無効であるか、ログインにデータベースでの CONNECT 権限がありません。  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER LOGIN を使用して、ログインの既定のデータベースを変更します。 CONNECT 権限をログインに許可します。  
  

