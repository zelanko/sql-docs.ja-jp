---
title: ODBC SQL 文法 (Visual FoxPro ODBC ドライバー) をサポート |Microsoft ドキュメント
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
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7eccb1bbdb86ded6b949756b4e5762a83a59fc0e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906917"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>サポートされている ODBC SQL 文法 (Visual FoxPro ODBC ドライバー)
Microsoft Visual FoxPro ODBC ドライバーには、次のサポートされています。  
  
-   すべての SQL ステートメントと、ODBC SQL の文法で句  
  
-   ODBC core SQL 文法から追加の SQL ステートメント  
  
 次の表は、ODBC SQL 文法レベルによって、ドライバーでサポートされている項目を一覧表示します。  
  
|レベル|要素|アイテム|  
|-----------|--------------|----------|  
|最小|データ定義言語 (DDL)|CREATE TABLE、および DROP TABLE|  
||データ操作言語 (DML)|選択、挿入、更新、および削除|  
||式|単純な (A など > + C)|  
||データ型|CHAR、VARCHAR、LONG VARCHAR|  
  
 だけでなく、サポートされている ODBC SQL 文法は、Visual FoxPro ODBC ドライバーは、次の Visual FoxPro コマンドの完全なネイティブ Visual FoxPro 言語構文をサポートします。  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [タグを削除します。](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
