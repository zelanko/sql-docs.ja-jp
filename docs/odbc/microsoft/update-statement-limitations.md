---
title: UPDATE ステートメントの制限事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 006d0f9644c9f62a6b50e2d327384ec3a9c954c1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
テーブルを更新する、Paradox ドライバーのテーブルに一意のインデックス (主キーの Paradox) ことが必要です。 Borland データベース エンジンを実装することがなく、Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストのドライバーによってサポートされていません。  
  
 Microsoft Excel ドライバーを使用する場合、値を更新することが、Microsoft Excel スプレッドシートに基づき、テーブルから行を削除できません。 その結果、UPDATE ステートメントでは、Microsoft Excel ドライバーで正式にサポートされているはありません。 INSERT ステートメントのみがサポートされていると見なされます。
