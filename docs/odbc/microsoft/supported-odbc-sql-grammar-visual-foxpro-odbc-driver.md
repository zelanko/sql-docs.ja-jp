---
title: サポートされている ODBC SQL 文法 (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f72548d0708a63f887f7d6da4d4f5988500f0eef
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304085"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>サポートされている ODBC SQL 文法 (Visual FoxPro ODBC ドライバー)
マイクロソフトビジュアル フォックスプロ ODBC ドライバーは、次をサポートしています。  
  
-   ODBC 最小 SQL 文法のすべての SQL ステートメントと句  
  
-   ODBC コア SQL 文法からの追加の SQL ステートメント  
  
 次の表は、ODBC SQL 文法レベルで、ドライバーでサポートされる項目の一覧です。  
  
|Level|Elements|Item|  
|-----------|--------------|----------|  
|最小値|データ定義言語 (DDL)|CREATE TABLE および DROP TABLE|  
||データ操作言語 (DML)|選択、挿入、更新、および削除|  
||式|シンプル (A>B+C など)|  
||データ型|CHAR、VARCHAR、または長いヴァルチャー|  
  
 サポートされている ODBC SQL 文法に加えて、Visual FoxPro ODBC ドライバーは、次の Visual FoxPro コマンドの完全なネイティブの Visual FoxPro 言語構文をサポートしています。  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [テーブルの作成](../../odbc/microsoft/create-table-sql-command.md)  
  
 [削除](../../odbc/microsoft/delete-sql-command.md)  
  
 [タグの削除](../../odbc/microsoft/delete-tag-command.md)  
  
 [テーブルをドロップする](../../odbc/microsoft/drop-table-command.md)  
  
 [インデックス](../../odbc/microsoft/index-command.md)  
  
 [挿入](../../odbc/microsoft/insert-sql-command.md)  
  
 [選択](../../odbc/microsoft/select-sql-command.md)  
  
 [更新](../../odbc/microsoft/update-sql-command.md)
