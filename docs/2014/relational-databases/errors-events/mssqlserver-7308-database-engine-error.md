---
title: MSSQLSERVER_7308 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e16da5c18dc1c23867a782144d7e48cb954b13f0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421131"
---
# <a name="mssqlserver7308"></a>MSSQLSERVER_7308
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7308|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|RMT_STA_DISABLED|  
|メッセージ テキスト|OLE DB プロバイダー '%ls' を分散クエリに使用することはできません。このプロバイダーは、シングル スレッド アパートメント モードで実行するように構成されています。|  
  
## <a name="explanation"></a>説明  
 シングル スレッド アパートメント (STA) モードで実行するように構成されている OLE DB プロバイダーを使用しました。 シングル スレッド アパートメント (STA) モードで実行する OLE DB プロバイダーを分散クエリに使用することはできません。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーを解決するには、プロバイダーをマルチスレッド アパートメント (MTA) モードで実行するように構成します。 プロバイダーが MTA をサポートしておらず、MTA をサポートするバージョンにアップグレードできない場合は、プロバイダーをプロセス外で実行するように構成することを検討してください。 プロバイダーが MTA またはプロセス外での実行をサポートしているかどうかは、プロバイダーの製造元に問い合わせてください。  
  
  
