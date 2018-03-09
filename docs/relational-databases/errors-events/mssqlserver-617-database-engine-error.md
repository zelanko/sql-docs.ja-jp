---
title: MSSQLSERVER_617 | Microsoft Docs
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
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aad0f7b77dbf806a9f8db57d134f5e662720988f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|617|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NODESHASH|  
|メッセージ テキスト|データベース ID %d のオブジェクト ID %ld の記述子の非ハッシュ化を試みたときに、記述子がハッシュ テーブルに見つかりませんでした。 作業テーブルがエントリに見つかりません。 クエリを再実行してください。 カーソルが含まれている場合は、カーソルを閉じてから再度開いてください。|  
  
## <a name="explanation"></a>説明  
SQL Server で、作業テーブルの特定のエントリが見つかりません。  
  
## <a name="user-action"></a>ユーザーの操作  
  
1.  カーソルが含まれている場合は、カーソルを閉じてから再度開いてください。  
  
2.  クエリを再実行します。  
  
