---
title: ブックマーク C データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 566f1065d30a47b2db234ba1f11f877725189fb7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292292"
---
# <a name="bookmark-c-data-type"></a>Bookmark C データ型
ブックマーク C データ型を使用すると、アプリケーションはブックマークを取得できます。 ブックマーク C 型は、長さが可変であるブックマーク値を取得するためだけに使用されます。他のデータ型に変換しないでください。 アプリケーションは **、SQLBulkOperations** (SQL_ADD操作を伴う) **、SQLFetch、SQLFetchScroll、** または**SQLGetData**を使用して、結果セットの列 0 からブックマークを取得します。 **SQLFetchScroll** 詳細については、「[ブックマーク](../../../odbc/reference/develop-app/bookmarks-odbc.md)」を参照してください。  
  
 次の表は、ブックマーク C データ型の*CType*の値、ブックマーク C データ型を実装する ODBC C データ型、および SQL からのこのデータ型の定義を示しています。H。  
  
> [!NOTE]
>  SQL_C_BOOKMARKデータ型は非推奨になりました。 ODBC *3.x*アプリケーションでは、SQL_C_BOOKMARKを使用しないでください。 ODBC *3.x*ドライバーは、ODBC *2.x*アプリケーションを使用する場合にのみ、SQL_C_BOOKMARKをサポートする必要があります。 ドライバー マネージャーは、アプリケーションが ODBC *2.x*ドライバーと連携する場合にSQL_C_BOOKMARKにSQL_C_VARBOOKMARKをマップします。  
  
|C 型識別子|ODBC C の型定義|C 型|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(非推奨)|ブックマーク|unsigned long int|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
