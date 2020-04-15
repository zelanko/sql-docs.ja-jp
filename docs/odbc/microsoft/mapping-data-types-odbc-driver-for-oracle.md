---
title: データ型のマッピング (Oracle 用 ODBC ドライバ) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 432c21b70efcdd63ef36bfe3d26f8488ddb11d1d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302673"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>データ型のマッピング (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle サーバーは、データ型のセットをサポートします。 Oracle 用の ODBC ドライバーは、これらのデータ型を適切な ODBC SQL データ型にマップします。 次の表に、Oracle 7.3 サーバーのデータ型と、対応する ODBC SQL データ型を示します。  
  
 Oracle 用 ODBC ドライバーは、Oracle 7.3 および一部の Oracle8 データ型をサポートしています。 サポートされる Oracle8 データ型の詳細については、「[サポートされるデータ型](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)」を参照してください。  
  
|Oracle サーバーのデータ型|ODBC SQL データ型|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  VARCHAR 列の許容サイズの詳細については、このガイドの[「VARCHAR 列サイズ](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md)」を参照してください。
