---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: faf43de11a0c1779f043c6dd854e361c0396dc6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913570"
---
# <a name="mssqlserver_7901"></a>MSSQLSERVER_7901
    
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
  
  
