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
manager: craigg
ms.openlocfilehash: a6b854cc417898c5576c60ca129c597eae280df4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826340"
---
# <a name="update-statement-limitations"></a>UPDATE ステートメントの制限事項
テーブルを更新する Paradox ドライバーの場合、テーブルに一意のインデックス (Paradox 主キー) ことが必要です。 Borland データベース エンジンを実装することがなく Paradox ドライバーを使用する場合、Paradox テーブルを更新することはできません。  
  
 テキストのドライバーによってサポートされていません。  
  
 Microsoft Excel のドライバーを使用する場合、値を更新することができますが、Microsoft Excel スプレッドシートに基づくテーブルから行を削除できません。 その結果、UPDATE ステートメントでは、Microsoft Excel のドライバーで正式にサポートはありません。 INSERT ステートメントのみがサポートされていると見なされます。
