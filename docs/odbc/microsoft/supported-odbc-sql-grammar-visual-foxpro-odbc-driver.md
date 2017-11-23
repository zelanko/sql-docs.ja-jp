---
title: "ODBC SQL 文法 (Visual FoxPro ODBC ドライバー) をサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2e5e1755f8c622efceac581e66168666fea9eb86
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
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
