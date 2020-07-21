---
title: MSSQLSERVER_7308 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be5b429c4827284ccec396760afbc1dceafb8c55
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551097"
---
# <a name="mssqlserver_7308"></a>MSSQLSERVER_7308
    
## <a name="details"></a>詳細  
  
|属性|値|  
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
  
  
