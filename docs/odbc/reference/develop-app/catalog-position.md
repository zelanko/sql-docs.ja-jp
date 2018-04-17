---
title: カタログの位置 |Microsoft ドキュメント
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8691e7a8f8e9f015f6c468f3deeb06973d017ab3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="catalog-position"></a>カタログの位置
識別子と識別子の残りの部分からの区切られた内のカタログ名の位置は、データ ソースにデータ ソースとは異なります。 たとえば、Xbase データ ソースにある、カタログ名ディレクトリし、Microsoft® Windows® で区切られてから、テーブル名 (ファイル名)、円記号 (\\)。 次の図では、この条件を示します。  
  
 ![カタログの位置: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 SQL Server データ ソースには、カタログはデータベースでありはスキーマとテーブルの名前から、ピリオド (.) で区切られます。  
  
 ![カタログの位置: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 Oracle データ ソースに、カタログもデータベースですが、テーブル名に依存し、は、スキーマとテーブル名から分離されて、アット マーク (@)。  
  
 ![カタログの位置: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 カタログの区切り記号とカタログ名の場所を指定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_NAME_SEPARATOR と SQL_CATALOG_LOCATION オプションを使用します。 相互運用可能アプリケーションは、これらの値に従って識別子を構築する必要があります。  
  
 1 つ以上の部分を含む識別子を引用符で囲むときにアプリケーションを各部分を個別に見積もりし、いない文字を識別子を区切る引用符で囲むように注意してくださいにする必要があります。 カタログ (\XBASE\SALES\CORP) とテーブル (Parts.dbf) の名前がカタログの区切り記号ではないなど、すべての行と Xbase テーブルの列を選択する次のステートメントを引用符で (\\)。  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 次のステートメントのすべての行および Oracle のテーブルの列の選択を引用符 (Sales)、カタログ、スキーマ (企業)、およびテーブル (部分) の名前がカタログではありません (@) またはスキーマ (.) の区切り記号。  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 識別子を引用符で囲む方法の詳細については、次のセクションを参照してください。[引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)です。
