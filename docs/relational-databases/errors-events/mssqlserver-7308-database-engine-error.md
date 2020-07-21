---
title: MSSQLSERVER_7308 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64e662ebf9354f3d1ff48bb5870bd19d367dea9c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780217"
---
# <a name="mssqlserver_7308"></a>MSSQLSERVER_7308
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
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
  
