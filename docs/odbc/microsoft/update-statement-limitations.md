---
title: "UPDATE ステートメントの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8746a3a54ba46b418262f94c0c19d778d718571f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
テーブルを更新する、Paradox ドライバーのテーブルに一意のインデックス (主キーの Paradox) ことが必要です。 Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストのドライバーによってサポートされていません。  
  
 Microsoft Excel ドライバーを使用する場合、値を更新することが、Microsoft Excel スプレッドシートに基づき、テーブルから行を削除できません。 その結果、UPDATE ステートメントでは、Microsoft Excel ドライバーで正式にサポートされているはありません。 INSERT ステートメントのみがサポートされていると見なされます。
