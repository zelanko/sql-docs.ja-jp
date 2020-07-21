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
ms.openlocfilehash: 6dd4d2721967049295f3fcf5fc8b38807268879a
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551059"
---
# <a name="mssqlserver_7901"></a>MSSQLSERVER_7901
    
## <a name="details"></a>詳細  
  
|属性|値|  
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
  
  
