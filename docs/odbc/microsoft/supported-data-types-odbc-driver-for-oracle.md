---
title: "サポートされるデータ型 (ODBC Driver for Oracle) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: af54700b80c2e2e2187f0c0b0ca5fe3a1137e374
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>サポートされるデータ型 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ODBC Driver for Oracle; Oracle 7.3 のすべてのデータ型をサポートしていますただし、次のとおり、新しい Oracle8 データ型のいずれかのこともできません。  
  
|データ型|Oracle 7.3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|n/a|サポートされていません|  
|BLOB|n/a|サポートされていません|  
|CHAR|Supported|Supported|  
|CLOB|n/a|サポートされていません|  
|[DATE]|Supported|Supported|  
|[FLOAT]|Supported|Supported|  
|INTEGER|Supported|Supported|  
|LONG|Supported|Supported|  
|LONG RAW|Supported|Supported|  
|NCHAR|n/a|サポートされていません|  
|NCLOB|n/a|サポートされていません|  
|NUMBER|Supported|Supported|  
|NVARCHAR2|n/a|サポートされていません|  
|RAW|Supported|Supported|  
|VARCHAR2|Supported|Supported|  
|MLSLABEL|サポートされていません。|サポートされていません。|  
  
> [!NOTE]  
>  VARCHAR 列の詳細については、許容サイズは、次を参照してください。 [VARCHAR 列サイズ](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md)このガイドでします。

