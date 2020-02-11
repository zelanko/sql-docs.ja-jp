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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d6d54d1fc7c7742bf94e91d7370f356e28b5624
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "71207688"
---
# <a name="odbc-data-sources-subkey"></a>ODBC データソースサブキー

サブキーの`ODBC Data Sources`下の値には、データソースが一覧表示されます。 これらの値の形式を次の表に示します。

| Name | データ型 | データ |
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
