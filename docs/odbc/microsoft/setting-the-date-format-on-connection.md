---
title: 接続で日付形式を設定する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date formats [ODBC]
- ODBC driver for Oracle [ODBC], date formats
ms.assetid: ba0d5123-db52-448b-8e19-b7647ce4b361
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3075893d37a401110afbecacc68e452425ad684b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063465"
---
# <a name="setting-the-date-format-on-connection"></a>接続時の日付形式の設定
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 新しいバージョンの Microsoft ODBC Driver for Oracle では、Oracle の日付フィールドの日付形式が自動的に設定されません。 以前は、ドライバーは接続さ`ALTER SESSION SET NLS_DATE_FORMAT ='YYYY-MM-DD HH:MI:SS'`れていました。  
  
 日付形式を設定するには、ALTER SESSION SET を呼び出し、挿入を実行します。 次に例を示します。  
  
```  
conn.Execute "ALTER SESSION SET NLS_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS' "  
sSql = "INSERT INTO DATETEST VALUES (24,'1988-12-01 10:23:03')"  
conn.Execute sSql  
```
