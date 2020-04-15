---
title: UPDATE ステートメントの制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ddf19c0b672901b2e778833f8bf624996d4ced3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307623"
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
Paradox ドライバがテーブルを更新するには、テーブルに一意のインデックス (Paradox 主キー) が必要です。 ボーランド データベース エンジンを実装せずに Paradox ドライバを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキスト ドライバではサポートされていません。  
  
 Microsoft Excel ドライバを使用する場合、値を更新することはできますが、Excel スプレッドシートを基にテーブルから行を削除することはできません。 その結果、UPDATE ステートメントは、Excel ドライバーによって正式にサポートされているとは見なされません。 INSERT ステートメントのみがサポートされていると見なされます。
