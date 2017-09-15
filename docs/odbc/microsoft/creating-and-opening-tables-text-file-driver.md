---
title: "作成して、テーブル (テキスト ファイル ドライバー) を開く |Microsoft ドキュメント"
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
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 41190a0a3eabda2f73c8f6046a64b7b7db929fa1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="creating-and-opening-tables-text-file-driver"></a>作成して、テーブル (テキスト ファイル ドライバー) を開く
テキストのドライバーを使用すると、Odbcinst.ini で指定された形式を使用して新しいテーブルが作成されます。 指定しない場合、CSVDELIMITED 形式でテーブルが作成されます。 既定では、11 文字に既定の整数型の列および FLOAT 列の既定値は 22 文字です。 日付の列では、YYYY-MM-DD の形式を使用します。 CHAR と LONGCHAR 列は、CREATE ステートメントで指定された幅がします。
