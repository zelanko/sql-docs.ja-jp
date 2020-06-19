---
title: MSSQLSERVER_1461 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6667728b2cc134632ddc538b662d73533ee4d6ef
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969542"
---
# <a name="mssqlserver_1461"></a>MSSQLSERVER_1461
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1461|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBM_SAFETY_MISMATCH|  
|メッセージ テキスト|データベース "%.*ls" で、データベース ミラーリングの安全性レベルがサーバー間で異なることが検出されました。 FULL 安全性レベルが使用されます。|  
  
## <a name="explanation"></a>説明  
 トランザクションの安全性設定がプリンシパル データベースとミラー データベースで一致しなかったため、トランザクションの安全性レベルの変更時にミラーリング接続が切断されました。 既定では、トランザクションの安全性が FULL の安全性設定が使用されます。 セッションは高い安全モードで実行されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 トランザクションの安全性を OFF に設定するには、プリンシパル データベースで ALTER DATABASE *database_name* SET PARTNER SAFETY OFF ステートメントを再実行します。  
  
  
