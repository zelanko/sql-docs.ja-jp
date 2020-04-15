---
title: サポートされるデータ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d19cde2d531819a60229dd7a780181571e169503
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307783"
---
# <a name="supported-data-types"></a>サポートされるデータ型
DBMS でサポートされるデータ型は、かなり異なります。 アプリケーションは **、 SQLGetTypeInfo**を呼び出すことによって、サポートされるデータ型の名前と特性を決定できます。 データ型名は多岐にわたるため、アプリケーションは**CREATE TABLE**ステートメントで**SQLGetTypeInfo**によって返されるデータ型名を使用する必要があります。 詳細については[、「ODBC でのデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)」を参照してください。
