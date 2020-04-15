---
title: 接続文字列を使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9083414503606720a40d372ed883a140953dc415
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307593"
---
# <a name="using-connection-strings"></a>接続文字列の使用
接続文字列を使用して、Visual FoxPro データ ソースに接続できます。  
  
 たとえば、TasTrade データ ソースに接続し、データ ソースに関連付けられている排他の現在の設定をオーバーライドするには、次の文字列を使用します。  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 接続文字列に含めることができる属性キーワードと値の一覧については、「 [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)」を参照してください。  
  
 接続文字列の構文の詳細については *、ODBC プログラマ リファレンス*の[SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md)を参照してください。
