---
title: MSSQLSERVER_9001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e61894d0d071fbdb36dcfb77895c46c61d0bbd1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85031451"
---
# <a name="mssqlserver_9001"></a>MSSQLSERVER_9001
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9001|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LOG_NOT_AVAIL|  
|メッセージ テキスト|データベース '%.*ls' のログは使用できません。 イベント ログで、関連するエラー メッセージを確認してください。 エラーがある場合は解決し、データベースを再起動してください。|  
  
## <a name="explanation"></a>説明  
 データベース ログがオフラインになりました。 通常、これは、データベースの再起動を必要とする重大なエラーを示しています。  
  
## <a name="user-action"></a>ユーザーの操作  
 他のエラーを診断し、まだ自動的に再起動されていない場合は SQL Server インスタンスを再起動します。  
  
  
