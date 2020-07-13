---
title: MSSQLSERVER_7920 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b974fda9619cd3819e79dc608d671c58e95419aa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726392"
---
# <a name="mssqlserver_7920"></a>MSSQLSERVER_7920
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|7920|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC2_SUMMARY_ENTRIES|  
|メッセージ テキスト|データベース ID D_ID のシステム カタログ内にある ENTRY_COUNT エントリを処理しました。|  
  
## <a name="explanation"></a>説明  
これは、DBCC CHECKALLOC 以外のすべての DBCC CHECK コマンドによって返される情報メッセージです。 返される値は、チェックされた行セットの合計数です。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
