---
title: カタログとスキーマの使用 |Microsoft ドキュメント
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0aa8e5c112bbd3bc807ecba821da2e754016b23a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="catalog-and-schema-usage"></a>カタログとスキーマの使用状況
データ ソースとは限りませんとしてサポートしていないカタログとスキーマ名オブジェクト名のすべての SQL ステートメントの識別子。 データ ソースは 1 つ以上の SQL ステートメントの次のクラスでカタログ名とスキーマ名をサポートする場合がありますデータ操作言語 (DML) ステートメント、プロシージャの呼び出し、テーブル定義ステートメント、インデックス定義ステートメント、および権限の定義。ステートメント。 カタログとスキーマのどの名を使用できる SQL ステートメントのクラスを確認するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_USAGE と SQL_SCHEMA_USAGE オプションを使用します。
