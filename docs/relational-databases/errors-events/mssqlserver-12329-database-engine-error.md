---
title: MSSQLSERVER_12329 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
caps.latest.revision: "4"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 772e884f81d682f72eb919db72f7a38330a89f60
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver12329"></a>MSSQLSERVER_12329
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|12329|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|HK_UNSUPPORTED_NON_LATIN_CODEPAGE|  
|メッセージ テキスト|1252 以外のコード ページを含む照合順序を使用するデータ型 char(n) および varchar(n) は、*construct* ではサポートされていません。|  
  
## <a name="explanation"></a>説明  
1252 以外のコード ページを含む照合順序を使用するデータ型 char(n) および varchar(n) は使用しないでください。  
  
## <a name="user-action"></a>ユーザーの操作  
このエラーが発生する可能性がある予期しない状況を次に示します。  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
代わりに、次を使用します。  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
