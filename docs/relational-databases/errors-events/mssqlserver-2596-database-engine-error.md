---
title: MSSQLSERVER_2596 | Microsoft Docs
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
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e16d2a73689ce73d49da4b36fe1569e95a750019
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2596"></a>MSSQLSERVER_2596
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2596|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|メッセージ テキスト|修復ステートメントは処理されませんでした。 データベースを読み取り専用モードにすることはできません。|  
  
## <a name="explanation"></a>説明  
このメッセージは、データベースが読み取り専用モードであることを示しています。 データベースが読み取り専用モードである場合は、修復が不可能です。  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER DATABASE を使用してデータベースを読み取り/書き込み可能に設定し、DBCC コマンドを再実行します。  
  
## <a name="see-also"></a>参照  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  
