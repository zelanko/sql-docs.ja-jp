---
title: ODBC データ ソース のサブキー |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbe6d0e7e424f2bea8d90eb4e9c5993f50370848
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-data-sources-subkey"></a>ODBC データ ソースのサブキー
ODBC データ ソースのサブキーの下の値には、データ ソースが一覧表示します。 これらの値の形式は、次の表に示すようにします。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|*データ ソース名*|REG_SZ|*ドライバーの説明*|  
  
 *データ ソース名*値は、管理プログラム (通常のユーザーを求められます)、によって定義と*ドライバーの説明*ドライバーの開発者によって定義されます (通常の名前は、DBMS ドライバーに関連付けられている)。  
  
 たとえば、3 つのデータ ソースが定義されている: SQL Server を使用して、インベントリ給与、dBASE; を使用します。スタッフが使用される形式のテキスト ファイルです。 ODBC データ ソースのサブキーの下の値が次のようにあります。  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
