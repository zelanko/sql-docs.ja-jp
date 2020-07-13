---
title: テーブルの作成とオープン (テキストファイルドライバー) |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280922"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>テーブルを作成して開く (テキスト ファイル ドライバー)
テキストドライバーが使用されている場合は、Odbcinst に指定された形式を使用して、新しいテーブルが作成されます。 指定しない場合、テーブルは CSVDELIMITED 形式で作成されます。 既定では、整数型の列の既定値は11文字で、FLOAT 型の列の既定値は22文字です。 日付列では、yyyy-mm-dd 形式が使用されます。 CHAR および LONGCHAR 列は、CREATE ステートメントで指定された幅です。
