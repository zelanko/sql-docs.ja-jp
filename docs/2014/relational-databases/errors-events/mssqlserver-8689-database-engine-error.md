---
title: MSSQLSERVER_8689 | Microsoft Docs
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
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c6716439038f61003abd807cefbf123ec3682b17
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174182"
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8689|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|USEPLAN_ERR_NO_DB|  
|メッセージ テキスト|USE PLAN ヒントで指定されたデータベース '%.*ls' は存在しません。 既存のデータベースを指定してください。|  
  
## <a name="explanation"></a>説明  
 USE PLAN ヒントで指定したデータベースが存在しません。  
  
## <a name="user-action"></a>ユーザーの操作  
 USE PLAN ヒントで指定したすべてのデータベースが存在することを確認します。  
  
## <a name="see-also"></a>参照  
 [クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)   
 [プラン ガイド](../performance/plan-guides.md)  
  
  
