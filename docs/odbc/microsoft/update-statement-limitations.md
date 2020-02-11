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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1cc8cf58d4e4d826dc4b152e395dedbea395a095
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088204"
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
Paradox ドライバーでテーブルを更新するには、テーブルに一意のインデックス (Paradox 主キー) が必要です。 Borland データベースエンジンを実装せずに Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストドライバーではサポートされていません。  
  
 Microsoft Excel driver が使用されている場合、値を更新することはできますが、Microsoft Excel スプレッドシートに基づくテーブルから行を削除することはできません。 その結果、UPDATE ステートメントは、Microsoft Excel ドライバーによって正式にサポートされているとは見なされません。 サポートされていると見なされるのは、INSERT ステートメントだけです。
