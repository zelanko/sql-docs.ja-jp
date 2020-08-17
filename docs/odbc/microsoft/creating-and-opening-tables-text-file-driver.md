---
description: テーブルを作成して開く (テキスト ファイル ドライバー)
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
ms.openlocfilehash: c64f74270e8c2bbf4645f72406113e88948d0da9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340968"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>テーブルを作成して開く (テキスト ファイル ドライバー)
テキストドライバーを使用すると、Odbcinst.ini で指定された形式を使用して新しいテーブルが作成されます。 指定しない場合、テーブルは CSVDELIMITED 形式で作成されます。 既定では、整数型の列の既定値は11文字で、FLOAT 型の列の既定値は22文字です。 日付列では、yyyy-mm-dd 形式が使用されます。 CHAR および LONGCHAR 列は、CREATE ステートメントで指定された幅です。
