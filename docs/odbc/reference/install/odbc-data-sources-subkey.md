---
title: ODBC データソースサブキー |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304061"
---
# <a name="odbc-data-sources-subkey"></a>ODBC データソースサブキー

サブキーの`ODBC Data Sources`下の値には、データソースが一覧表示されます。 これらの値の形式を次の表に示します。

| 名前 | データの種類 | データ |
| :--- | :-------- | :--- |
| *データソース名* | REG_SZ | *ドライバー-説明* |
| &nbsp; | &nbsp; | &nbsp; |

*データソース名*の値は、管理プログラムによって定義されます (通常はユーザーにプロンプトを表示します)。*ドライバーの説明*は、ドライバーの開発者によって定義されます (通常は、ドライバーに関連付けられている DBMS の名前です)。

たとえば、SQL Server を使用する Inventory という3つのデータソースが定義されているとします。DBASE を使用する Payroll書式設定されたテキストファイルを使用するスタッフ。 サブキーの`ODBC Data Sources`下の値は次のようになります。

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
