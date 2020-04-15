---
title: カタログとスキーマの使用 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306253"
---
# <a name="catalog-and-schema-usage"></a>カタログとスキーマの使用状況
データ ソースは、カタログ名とスキーマ名をすべての SQL ステートメントでオブジェクト名識別子としてサポートしている必要はありません。 データ・ソースは、データ操作言語 (DML) ステートメント、プロシージャー呼び出し、表定義ステートメント、索引定義ステートメント、および特権定義ステートメントの 1 つ以上のクラスのカタログおよびスキーマ名をサポートする場合があります。 カタログ名とスキーマ名を使用できる SQL ステートメントのクラスを判別するために、アプリケーションは**sqlGetInfo**をSQL_CATALOG_USAGEおよびSQL_SCHEMA_USAGEオプションとともに呼び出します。
