---
title: SQL 型の識別子 |Microsoft ドキュメント
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
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f3a9270e698f7f0ff12bd12c02de865a3c6f2b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-type-identifiers"></a>SQL 型の識別子
各データ ソースでは、独自の SQL データ型を定義します。 ODBC では、型識別子を定義し、各型の識別子にマップする可能性があります SQL データの種類の一般的な特性について説明します。 これは、ドライバー固有の ODBC SQL 型の識別子に、基になるデータ ソースの各データ型をマップする方法です。  
  
 たとえば、SQL_CHAR は、通常 1 ~ 254 文字の間の固定長文字型列の型識別子です。 これらの特性は、多くの SQL データ ソースで見つかった CHAR データ型に対応します。 したがって、アプリケーション検出すると、列の型識別子が SQL_CHAR である可能性があります、char 型の列を扱うことが想定できます。 ただし、まだチェックインと仮定すると、前に列のバイトの長さは、1 ~ 254 文字です。たとえば、非 SQL データ ソースのドライバーはどちらもために、SQL_CHAR または SQL_LONGVARCHAR の 500 文字の固定長文字型の列をマップ可能性がありますと完全に一致します。  
  
 ODBC では、さまざまな種類の SQL 識別子を定義します。 ただし、ドライバーでは、これらの識別子のすべてを使用する必要はありません。 代わりに、基になるデータ ソースでサポートされている SQL データ型を公開する必要がある識別子のみを使用します。 基になるデータ ソースには、SQL データ型がサポートされている場合は、どの型識別子のない対応、ドライバーは追加の型識別子を定義できます。 詳細については、次を参照してください。[ドライバー固有のデータ型、記述子の種類、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)です。  
  
 SQL 型識別子の詳細については、次を参照してください。 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: データ型にします。
