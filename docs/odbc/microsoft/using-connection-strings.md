---
title: "接続文字列の使用 |Microsoft ドキュメント"
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
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f95e0a2ed1b93e89254e5e357cc3889dc5817554
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-connection-strings"></a>接続文字列の使用
Visual FoxPro データ ソースに接続する接続文字列を使用することができます。  
  
 たとえば、TasTrade データ ソースとデータ ソースに関連付けられている排他の現在の設定の上書きに接続する場合、文字列を使用しました。  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 属性のキーワードと、接続文字列に含めることができます値の一覧は、次を参照してください。 [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)です。  
  
 接続文字列の構文の完全な説明については、次を参照してください。 [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md)で、 *ODBC プログラマ リファレンス*です。

