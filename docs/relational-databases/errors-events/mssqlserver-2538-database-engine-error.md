---
title: MSSQLSERVER_2538 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 44de009a70cfca53e6961fd1c06d7b39a1b8affd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045854"
---
# <a name="mssqlserver2538"></a>MSSQLSERVER_2538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2538|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_ALLOCATION_SUMMARY_PER_FILE|  
|メッセージ テキスト|ファイル FILE。 エクステント数 = EXTENTS、使用ページ数 = USED_PAGES、予約ページ数 = RESERVED_PAGES。|  
  
## <a name="explanation"></a>説明  
この情報は、DBCC CHECKALLOC コマンドからの出力の一部です。 この情報はファイルごとの要約であり、指定されたデータベースについて、割り当てられたエクステント数、使用ページ数、および予約ページ数を示します。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
