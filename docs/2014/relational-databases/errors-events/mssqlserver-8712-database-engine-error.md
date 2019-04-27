---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b956a9f51e013ce03801ff870e27f337c738b3c6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62762067"
---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8712|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|USEPLAN_ERR_NO_INDEX|  
|メッセージ テキスト|USE PLAN ヒントで指定したインデックス '%.*ls' が存在しません。 既存のインデックスを指定するか、指定した名前を持つインデックスを作成してください。|  
  
## <a name="explanation"></a>説明  
 USE PLAN ヒントで指定したインデックスが存在しません。  
  
## <a name="user-action"></a>ユーザーの操作  
 USE PLAN ヒントで指定したすべてのインデックスが存在することを確認します。  
  
## <a name="see-also"></a>関連項目  
 [クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)   
 [プラン ガイド](../performance/plan-guides.md)  
  
  
