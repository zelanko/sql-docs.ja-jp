---
title: カタログの位置 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0305d978dc4ecd21892a0be3916fa5072b7be95a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303383"
---
# <a name="catalog-position"></a>カタログの位置
識別子内のカタログ名の位置と、識別子の残りの部分との間のカタログ名の位置は、データ ソースによって異なります。 たとえば、Xbase データ ソースでは、カタログ名はディレクトリであり、Microsoft® では Windows® はテーブル名 (ファイル名) と円記号 ()\\で区切られます。 次の図は、この状態を示しています。  
  
 ![カタログの位置: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 SQL Server データ ソースでは、カタログはデータベースであり、スキーマ名とテーブル名からピリオド (.) で区切られます。  
  
 ![カタログの位置: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 Oracle データ・ソースでは、カタログはデータベースでもありますが、テーブル名の後に続き、スキーマ名とテーブル名とは、アットマーク (@) で区切られます。  
  
 ![カタログの位置: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 カタログの区切り記号とカタログ名の場所を決定するために、アプリケーションは**sqlGetInfo**をSQL_CATALOG_NAME_SEPARATORおよびSQL_CATALOG_LOCATIONオプションとともに呼び出します。 相互運用可能なアプリケーションは、これらの値に従って識別子を構築する必要があります。  
  
 複数の部分を含む識別子を引用する場合、アプリケーションは各部分を個別に引用し、識別子を区切る文字を引用符で囲まないように注意する必要があります。 たとえば、次のステートメントを使用して Xbase テーブルのすべての行と列を選択すると、カタログ (\XBASE\SALES\CORP) とテーブル (Parts.dbf) の名前が引用符で\\囲まれますが、カタログ区切り記号 ( ) は引用符で囲まれません。  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 次のステートメントを使用して、Oracle テーブルのすべての行と列を選択すると、カタログ (Sales)、スキーマ (企業)、テーブル (パーツ) の名前が引用符で囲まれますが、カタログ名またはスキーマ (.) の区切り記号は引用しません。  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 識別子の引用については、次のセクション「[引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)」を参照してください。
