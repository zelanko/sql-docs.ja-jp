---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 2c7e9da124ed3ec2fb1a0725f2f2c3050cd3484f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver9692"></a>MSSQLSERVER_9692
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9692|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SB2_CANT_LISTEN_PORT_IN_USE|  
|メッセージ テキスト|ポート %d は他のプロセスで使用中なので、%S_MSG プロトコルのトランスポートではそのポートでリッスンできません。|  
  
## <a name="explanation"></a>説明  
指定された TCP ポートが、コンピューター上の別のプログラムで使用されています。  
  
## <a name="user-action"></a>ユーザーの操作  
**netstat -aon** を実行して、このポートがどのプログラムで使用されているのかを調べます。 そのアプリケーションを無効にするか、Service Broker に対して別のポートを指定します。  
  
