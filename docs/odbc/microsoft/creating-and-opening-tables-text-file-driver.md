---
title: テーブルの作成と開き (テキスト ファイル ドライバ) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae13312299f131d1957557db28bbe4db0bf7b4c7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280922"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>テーブルを作成して開く (テキスト ファイル ドライバー)
テキスト ドライバーを使用すると、新しいテーブルが作成されます Odbcinst.ini で指定された形式を使用します。 指定しない場合、テーブルは CSVDELIMITED 形式で作成されます。 デフォルトでは、INTEGER カラムは 11 文字、FLOAT カラムはデフォルトで 22 文字です。 DATE 列は YYYY-MM-DD 形式を使用します。 CHAR 列と LONGCHAR 列は、CREATE ステートメントで指定された幅です。
