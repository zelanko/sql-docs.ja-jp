---
title: 接続文字列を使用する |Microsoft Docs
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
ms.openlocfilehash: 496fe10fbf49f4d712127e2e4122c50fa20ba2be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68044584"
---
# <a name="using-connection-strings"></a>接続文字列の使用
接続文字列を使用して、Visual FoxPro データソースに接続できます。  
  
 たとえば、TasTrade データソースに接続し、データソースに関連付けられているの現在の設定をオーバーライドするには、次の文字列を使用します。  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 接続文字列に含めることができる属性キーワードと値の一覧については、「 [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)」を参照してください。  
  
 接続文字列の構文の詳細については、 *ODBC プログラマーリファレンス*の[SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md)を参照してください。
