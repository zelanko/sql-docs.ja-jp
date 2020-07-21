---
title: カタログとスキーマの使用 |Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 245bd007f070a94689283830ba7a1362e31353e6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306253"
---
# <a name="catalog-and-schema-usage"></a>カタログとスキーマの使用状況
データソースは、すべての SQL ステートメントで、カタログ名とスキーマ名をオブジェクト名の識別子としてサポートするとは限りません。 データソースでは、データ操作言語 (DML) ステートメント、プロシージャ呼び出し、テーブル定義ステートメント、インデックス定義ステートメント、特権定義ステートメントなど、SQL ステートメントの1つ以上のクラスで、カタログ名とスキーマ名がサポートされている場合があります。 アプリケーションでは、カタログ名とスキーマ名を使用できる SQL ステートメントのクラスを特定するために、SQL_CATALOG_USAGE オプションと SQL_SCHEMA_USAGE オプションを使用して**SQLGetInfo**を呼び出します。
