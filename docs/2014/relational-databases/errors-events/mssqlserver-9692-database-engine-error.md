---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b740f7be7512f73bfe5c6d570ce3a97464a163fe
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553017"
---
# <a name="mssqlserver_9692"></a>MSSQLSERVER_9692
    
## <a name="details"></a>詳細  
  
|属性|値|  
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
 を実行し `netstat -aon` て、ポートを使用しているプログラムを特定します。 そのアプリケーションを無効にするか、Service Broker に対して別のポートを指定します。  
  
  
