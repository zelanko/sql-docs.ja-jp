---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a5d59ea61cff7051c3e1163a463c29443c553923
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033525"
---
# <a name="mssqlserver_3413"></a>MSSQLSERVER_3413
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3413|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|MARKDB|  
|メッセージ テキスト|データベース ID %d。 データベースを問題ありに設定できませんでした。 sys.databases.database_id での Getnext NC スキャンが失敗しました。 エラー ログで以前のエラーを参照して原因を特定し、関連している問題をすべて修正してください。|  
  
## <a name="explanation"></a>説明  
 カタログ内で、ユーザー データベースを SUSPECT に設定しようとして、予期しないエラーが発生しました。 SUSPECT 状態は保存されません。  
  
## <a name="user-action"></a>ユーザーの操作  
 これより前に発生したエラーを調べて、問題を修正します。  
  
  
