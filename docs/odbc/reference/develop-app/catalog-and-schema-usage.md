---
title: "カタログとスキーマの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 217f68d674dc7099b741e77d287ca81fcc2688e5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-and-schema-usage"></a>カタログとスキーマの使用状況
データ ソースとは限りませんとしてサポートしていないカタログとスキーマ名オブジェクト名のすべての SQL ステートメントの識別子。 データ ソースは 1 つ以上の SQL ステートメントの次のクラスでカタログ名とスキーマ名をサポートする場合がありますデータ操作言語 (DML) ステートメント、プロシージャの呼び出し、テーブル定義ステートメント、インデックス定義ステートメント、および権限の定義。ステートメント。 カタログとスキーマのどの名を使用できる SQL ステートメントのクラスを確認するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_USAGE と SQL_SCHEMA_USAGE オプションを使用します。

