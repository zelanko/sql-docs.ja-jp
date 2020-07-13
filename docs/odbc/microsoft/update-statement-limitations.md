---
title: UPDATE ステートメントの制限事項 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307623"
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
Paradox ドライバーでテーブルを更新するには、テーブルに一意のインデックス (Paradox 主キー) が必要です。 Borland データベースエンジンを実装せずに Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストドライバーではサポートされていません。  
  
 Microsoft Excel driver が使用されている場合、値を更新することはできますが、Microsoft Excel スプレッドシートに基づくテーブルから行を削除することはできません。 その結果、UPDATE ステートメントは、Microsoft Excel ドライバーによって正式にサポートされているとは見なされません。 サポートされていると見なされるのは、INSERT ステートメントだけです。
