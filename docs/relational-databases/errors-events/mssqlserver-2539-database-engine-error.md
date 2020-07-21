---
title: MSSQLSERVER_2539 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d270c016d60be484e6dbd81127006e56572a3cb6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780296"
---
# <a name="mssqlserver_2539"></a>MSSQLSERVER_2539
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|2539|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_ALLOCATION_SUMMARY_FOR_DATABASE|  
|メッセージ テキスト|このデータベース内のエクステントの合計数 = EXTENTS、使用ページ数 = USED_PAGES、および予約ページ数 = RESERVED_PAGES。|  
  
## <a name="explanation"></a>説明  
この情報は、DBCC CHECKALLOC コマンドからの出力の一部です。 この情報は、指定されたデータベースについて、割り当てられたエクステント数、使用ページ数、および予約ページ数を示す要約です。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
