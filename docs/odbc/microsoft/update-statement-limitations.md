---
title: "UPDATE ステートメントの制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 828fc042a4184bfedccf7c26210f899c1d73f2a4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
テーブルを更新する、Paradox ドライバーのテーブルに一意のインデックス (主キーの Paradox) ことが必要です。 Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストのドライバーによってサポートされていません。  
  
 Microsoft Excel ドライバーを使用する場合、値を更新することが、Microsoft Excel スプレッドシートに基づき、テーブルから行を削除できません。 その結果、UPDATE ステートメントでは、Microsoft Excel ドライバーで正式にサポートされているはありません。 INSERT ステートメントのみがサポートされていると見なされます。

