---
title: サポートされるデータ型 (ODBC Driver for Oracle) |Microsoft ドキュメント
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
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9863c45a3667d9c6b211a0a62d7577bb3189644d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
