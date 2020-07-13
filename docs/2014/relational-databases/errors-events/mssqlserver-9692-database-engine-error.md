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
ms.openlocfilehash: 6b6ba95771aafffa5a322ffa1b7443419936addd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053434"
---
# <a name="mssqlserver_9692"></a>MSSQLSERVER_9692
    
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
 を実行し `netstat -aon` て、ポートを使用しているプログラムを特定します。 そのアプリケーションを無効にするか、Service Broker に対して別のポートを指定します。  
  
  
