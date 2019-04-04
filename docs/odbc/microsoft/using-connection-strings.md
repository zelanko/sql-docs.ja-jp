---
title: 接続文字列の使用 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77bc54f857e04f31ccb982ca40b3ed6334664870
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848776"
---
# <a name="using-connection-strings"></a>接続文字列の使用
Visual FoxPro データ ソースに接続する接続文字列を使用することができます。  
  
 たとえば、TasTrade データ ソースとデータ ソースに関連付けられている排他の現在の設定の上書きに接続するには、文字列を使用します。  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 一連の属性のキーワードと値、接続文字列に含めることができます、[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)を参照してください。  
  
 接続文字列の構文の詳細については、[SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md)で、 *ODBC プログラマ リファレンス*を参照してください。
