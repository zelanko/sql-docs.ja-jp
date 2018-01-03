---
title: "ドライバー固有の型のデータ、記述子については、診断 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver-specific diagnostic values [ODBC]
- diagnostic information [ODBC], driver-specific values
- ODBC drivers [ODBC], driver-specific diagnostic values
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 184ad1369e8f37def7baa2f1ed8ff4677b2a85f5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>ドライバー固有のデータ型、記述子の種類、情報の種類、診断型、および属性
ドライバーは、次のドライバー固有の値を割り当てることができます。  
  
-   **SQL データ型を表すインジケーター**のために使用されます*ParameterType*で**SQLBindParameter**し、 *DataType*で**SQLGetTypeInfo**によって返されると**SQLColAttribute**、 **SQLColumns**、 **SQLDescribeCol**、 **SQLGetTypeInfo**、 **SQLDescribeParam**、 **SQLProcedureColumns**、および**SQLSpecialColumns**です。  
  
-   **記述子フィールド**のために使用されます*FieldIdentifier*で**SQLColAttribute**、 **SQLGetDescField**、および**SQLSetDescField**.  
  
-   **診断フィールド**のために使用されます*DiagIdentifier*で**SQLGetDiagField**と**SQLGetDiagRec**です。  
  
-   **情報の種類**のために使用されます*情報の種類*で**SQLGetInfo**です。  
  
-   **接続とステートメント属性**のために使用されます*属性*で**SQLGetConnectAttr**、 **SQLGetStmtAttr**、 **SQLSetConnectAttr**、および**SQLSetStmtAttr**です。  
  
 2 つの値のセットがあるこれらの項目のそれぞれについて、: ODBC で使用するために予約値と値のドライバーで使用するために予約されています。 ドライバー固有の値を実装する前にドライバー ライターは、Open Group から各ドライバー固有の型、フィールド、または属性の値を要求する必要があります。 新しいドライバーの開発では、次の表で説明されている範囲を使用します。 次に示す範囲に含まれていない、不明な値を使用する場合、ODBC 3.8 ドライバー マネージャーはエラーを生成しません。 ただし、以降のバージョンのドライバー マネージャーは、不明な値が受信した範囲に含まれていない場合、エラーを生成可能性があります。  
  
 これらの値のいずれかが ODBC 関数に渡されるときに、ドライバーが、値が有効かどうかをチェックする必要があります。 ドライバーは SQLSTATE HYC00 を返します (省略可能な機能が実装されていません) の他のドライバーに適用されるドライバー固有の値。  
  
 以降で ODBC 3.8 は、ドライバーの作成者は、予約済みの範囲内でのドライバー固有の属性を割り当てることができます。  
  
> [!NOTE]  
>  ODBC 3.8 ドライバー マネージャーは、検証も、旧バージョンとの互換性のため、これらの範囲を適用します。 ただし、今後のバージョンのドライバー マネージャーを適用、可能性があります。  
  
|属性の型|ODBC データ型|基本ドライバー固有の範囲|ドライバー固有の範囲の制限|ドライバー固有の値範囲ベースの ODBC 定数|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|SQL データ型を表すインジケーター|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|記述子フィールド|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|診断フィールド|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|情報の種類|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|接続属性|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|ステートメント属性|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  ドライバー固有のデータ型、記述子フィールド、診断フィールド、情報の種類、ステートメント属性および接続属性は、ドライバーのドキュメントで説明する必要があります。 これらの値のいずれかが ODBC 関数に渡されるときに、ドライバーが、値が有効かどうかをチェックする必要があります。 ドライバーは SQLSTATE HYC00 を返します (省略可能な機能が実装されていません) の他のドライバーに適用されるドライバー固有の値。  
  
 基本の値は、ドライバーの開発を容易にするために定義されます。 たとえば、ドライバー固有の診断属性は、次の形式で定義できます。  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
