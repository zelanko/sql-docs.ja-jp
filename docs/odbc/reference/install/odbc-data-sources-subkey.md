---
title: ODBC データ ソース サブキー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 09/23/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c5e97e643a78187b15e91833c832cd16ca435c7f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304061"
---
# <a name="odbc-data-sources-subkey"></a>ODBC データ ソース サブキー

サブキーの下`ODBC Data Sources`の値には、データ ソースが一覧表示されます。 これらの値の形式を次の表に示します。

| 名前 | データ型 | Data |
| :--- | :-------- | :--- |
| *データ ソース名* | REG_SZ | *ドライバーの説明* |
| &nbsp; | &nbsp; | &nbsp; |

*データ ソース名*の値は管理プログラム (通常はユーザーに要求する) によって定義され、*ドライバーの説明*はドライバー開発者によって定義されます (通常は、ドライバーに関連付けられている DBMS の名前です)。

たとえば、3 つのデータ ソースが定義されているとします。dBASE を使用する給与。および、書式設定されたテキスト ファイルを使用する担当者。 サブキーの下`ODBC Data Sources`の値は次のようになります。

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
