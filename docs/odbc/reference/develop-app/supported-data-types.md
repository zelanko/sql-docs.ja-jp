---
title: サポートされるデータ型 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307783"
---
# <a name="supported-data-types"></a>サポートされるデータ型
Dbms でサポートされるデータ型は大きく異なります。 アプリケーションでは、 **SQLGetTypeInfo**を呼び出すことによって、サポートされているデータ型の名前と特性を判断できます。 データ型名にはさまざまなバリエーションがあるため、アプリケーションは**CREATE TABLE**ステートメントで**SQLGetTypeInfo**によって返されるデータ型名を使用する必要があります。 詳細については、「 [ODBC のデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)」を参照してください。
