---
title: UPDATE ステートメントの制限事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbb1e6cbf0660f7b016391d5881b77d7e89e1f81
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
テーブルを更新する、Paradox ドライバーのテーブルに一意のインデックス (主キーの Paradox) ことが必要です。 Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストのドライバーによってサポートされていません。  
  
 Microsoft Excel ドライバーを使用する場合、値を更新することが、Microsoft Excel スプレッドシートに基づき、テーブルから行を削除できません。 その結果、UPDATE ステートメントでは、Microsoft Excel ドライバーで正式にサポートされているはありません。 INSERT ステートメントのみがサポートされていると見なされます。
