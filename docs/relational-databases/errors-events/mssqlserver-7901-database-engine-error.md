---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d3eeee976a45817b155c86ae99bd2cbd229324d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62694456"
---
# <a name="mssqlserver7901"></a>MSSQLSERVER_7901
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7901|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|メッセージ テキスト|修復ステートメントは処理されませんでした。 データベースが緊急モードのときは、このレベルの修復はサポートされません。|  
  
## <a name="explanation"></a>説明  
データベースが緊急モードであり、REPAIR_ALLOW_DATA_LOSS 以外の修復レベルが指定されました。 REPAIR_ALLOW_DATA_LOSS が指定されていない場合に、緊急モードで修復を実行することはできません。  
  
## <a name="user-action"></a>ユーザーの操作  
REPAIR_ALLOW_DATA_LOSS オプションを指定して、コマンドを再実行します。  
  
