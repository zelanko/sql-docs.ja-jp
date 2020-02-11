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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5ec0f3943fd52540f094a23e9b3f9f3886e1371
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114075"
---
# <a name="supported-data-types"></a>サポートされるデータ型
Dbms でサポートされるデータ型は大きく異なります。 アプリケーションでは、 **SQLGetTypeInfo**を呼び出すことによって、サポートされているデータ型の名前と特性を判断できます。 データ型名にはさまざまなバリエーションがあるため、アプリケーションは**CREATE TABLE**ステートメントで**SQLGetTypeInfo**によって返されるデータ型名を使用する必要があります。 詳細については、「 [ODBC のデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)」を参照してください。
