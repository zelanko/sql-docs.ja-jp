---
title: "カタログとスキーマの使用 |Microsoft ドキュメント"
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6653d44ad75fb9e2d1941a6d280ba0ec91dd275d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="catalog-and-schema-usage"></a>カタログとスキーマの使用状況
データ ソースとは限りませんとしてサポートしていないカタログとスキーマ名オブジェクト名のすべての SQL ステートメントの識別子。 データ ソースは 1 つ以上の SQL ステートメントの次のクラスでカタログ名とスキーマ名をサポートする場合がありますデータ操作言語 (DML) ステートメント、プロシージャの呼び出し、テーブル定義ステートメント、インデックス定義ステートメント、および権限の定義。ステートメント。 カタログとスキーマのどの名を使用できる SQL ステートメントのクラスを確認するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_USAGE と SQL_SCHEMA_USAGE オプションを使用します。
