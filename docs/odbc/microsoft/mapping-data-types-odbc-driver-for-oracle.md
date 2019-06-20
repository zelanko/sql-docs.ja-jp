---
title: データ型 (ODBC Driver for Oracle) のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecdd7d7d4b597c4cae218e18b40b0f78e27a6bd5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026877"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>データ型のマッピング (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle サーバーには、データ型のセットがサポートしています。 ODBC Driver for Oracle では、これらのデータ型を適切な ODBC SQL データ型にマップします。 次の表は、Oracle 7.3 のサーバーのデータ型とその対応する ODBC SQL データ型を示します。  
  
 ODBC Driver for Oracle では、Oracle 7.3、Oracle8 一部のデータ型をサポートします。 サポートされている Oracle8 データの種類の詳細については、次を参照してください。 [Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)します。  
  
|Oracle サーバーのデータ型|ODBC SQL データ型|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|[DATE]|SQL_TIMESTAMP|  
|[FLOAT]|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  VARCHAR 列の許容サイズの詳細については、次を参照してください。 [VARCHAR 列のサイズ](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md)このガイドでします。
