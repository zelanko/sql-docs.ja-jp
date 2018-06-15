---
title: 作成して、テーブル (テキスト ファイル ドライバー) を開く |Microsoft ドキュメント
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
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b836fa5144ffb59a155eed150f3372385d808343
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899627"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>作成して、テーブル (テキスト ファイル ドライバー) を開く
テキストのドライバーを使用すると、Odbcinst.ini で指定された形式を使用して新しいテーブルが作成されます。 指定しない場合、CSVDELIMITED 形式でテーブルが作成されます。 既定では、11 文字に既定の整数型の列および FLOAT 列の既定値は 22 文字です。 日付の列では、YYYY-MM-DD の形式を使用します。 CHAR と LONGCHAR 列は、CREATE ステートメントで指定された幅がします。
