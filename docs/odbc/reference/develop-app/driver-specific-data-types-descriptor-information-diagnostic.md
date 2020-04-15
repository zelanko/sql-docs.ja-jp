---
title: ドライバ固有の型 - データ、記述子、情報、診断 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver-specific diagnostic values [ODBC]
- diagnostic information [ODBC], driver-specific values
- ODBC drivers [ODBC], driver-specific diagnostic values
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19bb2dd113fbeae871892ea510713c638c886e5a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305769"
---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>ドライバー固有のデータ型、記述子の種類、情報の種類、診断型、および属性
ドライバーは、次のドライバー固有の値を割り当てることができます。  
  
-   **SQL データ型インジケータ**これらは **、SQL バインドパラメーター**の*パラメーター型*と**SQLGetTypeInfo**の*データ型*で使用され **、SQLCol 属性**、SQLColumns、SQLDescribeCol、SQLGetTypeInfo、SQLDescribeParam、SQLProcedureColumns 、および**SQLDescribeParam****SQLColumns****SQLGetTypeInfo****SQLSpecialColumns**によって返されます。 **SQLDescribeCol** **SQLProcedureColumns**  
  
-   **記述子フィールド**これらは **、SQLCol 属性****、SQLGetDesc フィールド**、および**SQLSetDescField**の*フィールド識別子*で使用されます。  
  
-   **診断フィールド**これらは **、SQLGetDiagField**および**SQLGetDiagRec**の*DiagIdentifier*で使用されます。  
  
-   **情報の種類**これらは、 **SQLGetInfo**の*インフォタイプ*で使用されます。  
  
-   **接続とステートメントの属性**これらは **、SQLGetConnectAttr** **、SQLGetStmtAttr、** および**SQLSetStmtAttr**の**SQLSetStmtAttr***属性*で使用されます。  
  
 これらの項目ごとに、ODBC で使用するために予約されている値と、ドライバーが使用するために予約されている値の 2 つの値セットがあります。 ドライバー固有の値を実装する前に、ドライバーの作成者は、Open Group から各ドライバー固有の型、フィールド、または属性の値を要求する必要があります。 新しいドライバ開発の場合は、次の表に示す範囲を使用します。 ODBC 3.8 ドライバ マネージャは、以下に説明する範囲にない未知の値を使用してもエラーを生成しません。 ただし、範囲外の不明な値を受け取った場合、ドライバー マネージャーの新しいバージョンでエラーが生成される可能性があります。  
  
 これらの値のいずれかが ODBC 関数に渡された場合、ドライバーは値が有効かどうかを確認する必要があります。 ドライバーは、他のドライバーに適用されるドライバー固有の値の SQLSTATE HYC00 (実装されていないオプション機能) を返します。  
  
 ODBC 3.8 以降では、ドライバーの作成者は、予約された範囲内でドライバー固有の属性を割り当てることができます。  
  
> [!NOTE]  
>  ODBC 3.8 ドライバ マネージャは、下位互換性のためにこれらの範囲を検証したり、適用したりしません。 ただし、将来のバージョンのドライバー マネージャーで強制する可能性があります。  
  
|属性の型|ODBC データ型|ドライバ固有の範囲ベース|ドライバ固有の範囲制限|ドライバー固有の値範囲のベースの ODBC 定数|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|SQL データ・タイプ標識|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|記述子フィールド|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|診断フィールド|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|情報の種類|スモートフィント|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|接続属性|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|ステートメント属性|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  ドライバー固有のデータ型、記述子フィールド、診断フィールド、情報の種類、ステートメント属性、および接続属性については、ドライバーのドキュメントで説明する必要があります。 これらの値のいずれかが ODBC 関数に渡された場合、ドライバーは値が有効かどうかを確認する必要があります。 ドライバーは、他のドライバーに適用されるドライバー固有の値の SQLSTATE HYC00 (実装されていないオプション機能) を返します。  
  
 基本値は、ドライバーの開発を容易にするために定義されます。 たとえば、ドライバー固有の診断属性は、次の形式で定義できます。  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
