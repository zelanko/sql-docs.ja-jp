---
title: "UPDATE ステートメントの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
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
ms.openlocfilehash: 502315916781ae5624f94e099c0cd95c52ffe8a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
テーブルを更新する、Paradox ドライバーのテーブルに一意のインデックス (主キーの Paradox) ことが必要です。 Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストのドライバーによってサポートされていません。  
  
 Microsoft Excel ドライバーを使用する場合、値を更新することが、Microsoft Excel スプレッドシートに基づき、テーブルから行を削除できません。 その結果、UPDATE ステートメントでは、Microsoft Excel ドライバーで正式にサポートされているはありません。 INSERT ステートメントのみがサポートされていると見なされます。
