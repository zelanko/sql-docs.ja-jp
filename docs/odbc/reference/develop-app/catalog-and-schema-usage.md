---
title: カタログとスキーマの使用状況 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9476f4f928890514354f97ce604f871bd8a06d11
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007890"
---
# <a name="catalog-and-schema-usage"></a>カタログとスキーマの使用状況
データ ソースが、すべての SQL ステートメント内でのオブジェクト名の識別子としてのカタログとスキーマ名を必ずしもにサポートしません。 データ ソースは、SQL ステートメントの次のクラスの 1 つ以上のカタログとスキーマ名をサポートする場合があります。データ操作言語 (DML) ステートメント、プロシージャの呼び出し、テーブル定義ステートメント、インデックス定義ステートメント、および特権定義ステートメント。 カタログとスキーマ名を使用できる SQL ステートメントのクラスを確認するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_USAGE および SQL_SCHEMA_USAGE のオプションを使用します。
