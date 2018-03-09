---
title: MSSQLSERVER_5231 | Microsoft Docs
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
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a9776a1055598f10e17470bb13eb713173441221
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5231|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|メッセージ テキスト|オブジェクト ID O_ID (オブジェクト 'NAME') : このオブジェクトを確認のためにロックしようとして、デッドロックが発生しました。 このオブジェクトはスキップされたので、処理されません。|  
  
## <a name="explanation"></a>説明  
DBCC がオブジェクトをロックしようとしてデッドロックが発生し、DBCC がデッドロック対象として選択されました。 このオブジェクトは処理されません。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
