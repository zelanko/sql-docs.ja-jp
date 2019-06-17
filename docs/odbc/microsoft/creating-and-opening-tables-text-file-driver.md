---
title: 作成して、テーブル (テキスト ファイル ドライバー) を開く |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce901e6a8639c8a2caea6e55cbaa18fedb56f4a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63132724"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>テーブルを作成して開く (テキスト ファイル ドライバー)
テキストのドライバーを使用すると、Odbcinst.ini で指定された形式を使用して新しいテーブルが作成されます。 指定しない場合、CSVDELIMITED 形式でテーブルが作成されます。 既定では、既定を 11 文字の整数型の列および FLOAT 列の既定値は 22 文字。 日付列では、YYYY-MM-DD の形式を使用します。 CHAR と LONGCHAR 列は、CREATE ステートメントで指定された幅です。
