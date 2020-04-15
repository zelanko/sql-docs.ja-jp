---
title: SQL 型識別子 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 95bf46844e9ed91aac1ec6cb93a298995f0901d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299772"
---
# <a name="sql-type-identifiers"></a>SQL の型識別子
各データ ソースは、独自の SQL データ型を定義します。 ODBC は型識別子を定義し、各型識別子にマップされる可能性のある SQL データ型の一般的な特性を記述します。 基になるデータ ソースの各データ型が、ODBC の SQL 型識別子にマップされる方法は、ドライバー固有です。  
  
 たとえば、SQL_CHARは固定長の文字列の型識別子で、通常は 1 ~ 254 文字です。 これらの特性は、多くの SQL データ・ソースに見られる CHAR データ・タイプに対応しています。 したがって、アプリケーションが列の型識別子がSQL_CHARであることを検出すると、おそらく CHAR 列を扱っていると見なすことができます。 ただし、1 から 254 文字の間であると想定する前に、列のバイト長をチェックする必要があります。たとえば、SQL 以外のデータ ソースのドライバーは、どちらも完全に一致しないため、500 文字の固定長の文字列を SQL_CHAR またはSQL_LONGVARCHARにマップする場合があります。  
  
 ODBC では、さまざまな SQL 型識別子を定義します。 ただし、ドライバーは、これらの識別子のすべてを使用する必要はありません。 代わりに、基になるデータ ソースでサポートされる SQL データ型を公開するために必要な識別子のみを使用します。 基になるデータ ソースが、型識別子が対応しない SQL データ型をサポートしている場合、ドライバーは追加の型識別子を定義できます。 詳細については、「[ドライバ固有のデータ型、記述子の型、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)」を参照してください。  
  
 SQL タイプ識別子の詳細については、「付録 D: データ型」の[C データ型](../../../odbc/reference/appendixes/c-data-types.md)を参照してください。
