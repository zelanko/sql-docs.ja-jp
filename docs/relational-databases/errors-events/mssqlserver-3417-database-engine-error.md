---
title: MSSQLSERVER_3417 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: c97cd13d12af2fbfc4c0bb413b36e25b6fba87cd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver3417"></a>MSSQLSERVER_3417
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3417|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|REC_BADMASTER|  
|メッセージ テキスト|master データベースを復旧できません。 SQL Server を実行できません。 master データベースを、完全バックアップを使用して復元するか、修復または再構築してください。 master データベースを再構築する方法の詳細については、SQL Server オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
SQL Server は **master** データベースを起動できません。 **master** または **tempdb** がオンライン状態にならないと、SQL Server は稼働しません。 このエラーは通常、別のエラーの後に発生します。 エラー ログで、根本的な原因を確認してください。  
  
## <a name="user-action"></a>ユーザーの操作  
データベースのバックアップを復元するか、データベースを修復します。  
  
