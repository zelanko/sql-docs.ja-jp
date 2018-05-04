---
title: DELETE ステートメントの制限事項 |Microsoft ドキュメント
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
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c731ba4a7482e981e0674c5d108115fc0960cd9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="delete-statement-limitations"></a>ステートメントの制限を削除します。
DELETE ステートメントは、Microsoft Excel またはテキストのドライバーのサポートされていません。 INSERT ステートメントがテキスト ドライバーのサポートされていることに注意してください。  
  
 DBASE ドライバーは、パッキング値の「削除」を削除するテーブルをサポートしていません。  
  
 テーブルから行を削除する、Paradox ドライバーのテーブルに一意のインデックス (主キーの Paradox) ことが必要です。
