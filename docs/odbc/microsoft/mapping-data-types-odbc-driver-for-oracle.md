---
title: データ型 (ODBC Driver for Oracle) のマッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92e8df65faf6be2cbe7d63d00e922ac1c4ed3af2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>データ型のマッピング (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle サーバーでは、一連のデータ型をサポートします。 ODBC Driver for Oracle は、これらのデータ型を適切な ODBC SQL データ型にマップされます。 次の表には、Oracle 7.3 サーバーのデータ型とその対応する ODBC SQL データ型が一覧表示します。  
  
 ODBC Driver for Oracle には、Oracle 7.3、Oracle8 データ型がサポートしています。 サポートされている Oracle8 データ型の詳細については、次を参照してください。 [Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)です。  
  
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
>  VARCHAR 列の詳細については、許容サイズは、次を参照してください。 [VARCHAR 列サイズ](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md)このガイドでします。
