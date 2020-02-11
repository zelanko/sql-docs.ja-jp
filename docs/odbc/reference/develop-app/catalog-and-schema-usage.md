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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e10460df120451502d798376453d69d111051ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064414"
---
# <a name="catalog-and-schema-usage"></a>カタログとスキーマの使用状況
データソースは、すべての SQL ステートメントで、カタログ名とスキーマ名をオブジェクト名の識別子としてサポートするとは限りません。 データソースでは、次の SQL ステートメントの1つ以上のクラスでカタログ名とスキーマ名がサポートされている場合があります。データ操作言語 (DML) ステートメント、プロシージャ呼び出し、テーブル定義ステートメント、インデックス定義ステートメント、および特権定義命令. アプリケーションでは、カタログ名とスキーマ名を使用できる SQL ステートメントのクラスを特定するために、SQL_CATALOG_USAGE オプションと SQL_SCHEMA_USAGE オプションを使用して**SQLGetInfo**を呼び出します。
