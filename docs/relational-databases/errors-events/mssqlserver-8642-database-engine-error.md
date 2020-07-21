---
title: MSSQLSERVER_8642 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ced4c9b3e690b709be9d8f500ff2656cf6b5e220
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727430"
---
# <a name="mssqlserver_8642"></a>MSSQLSERVER_8642
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|8642|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|EXCHNGSTART_ERR|  
|メッセージ テキスト|クエリ プロセッサは、クエリの並列実行に必要なスレッド リソースを開始できませんでした。|  
  
## <a name="explanation"></a>説明  
サーバー上のスレッド リソースが不足しています。  
  
## <a name="user-action"></a>ユーザーの操作  
サーバーの負荷を軽減してからクエリを再実行します。  
  
