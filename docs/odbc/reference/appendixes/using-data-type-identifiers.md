---
title: データ型識別子を使用して |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f14294b76fc7977de256697c730f7dca31e7a469
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516611"
---
# <a name="using-data-type-identifiers"></a>データ型識別子の使用
アプリケーションでは、2 つの方法でデータ型識別子を使用します。 ドライバーにバッファーを記述すると、結果を使用してデータを格納するバッファーの C の種類を判別できるように、ドライバーからセットに関するメタデータを取得します。 アプリケーションでは、これらのタスクを実行するには、次の関数を呼び出します。  
  
-   **SQLBindParameter**、 **SQLBindCol**、および**SQLGetData** - アプリケーションのバッファーの C データ型を記述します。  
  
-   **SQLBindParameter** - 動的パラメーターの SQL データ型を記述します。  
  
-   **SQLColAttribute**と**SQLDescribeCol** - 結果セット列の SQL データ型を取得します。  
  
-   **SQLDescribeParameter** - パラメーターの SQL データ型を取得します。  
  
-   **SQLColumns**、 **SQLProcedureColumns**、および**SQLSpecialColumns** - さまざまなスキーマ情報の SQL データ型を取得するには  
  
-   **SQLGetTypeInfo** - サポートされるデータ型の一覧を取得するには  
  
 データ型識別子は、記述子の SQL_DESC_CONCISE_TYPE フィールドに格納されます。 記述子関数**SQLSetDescField**と**SQLSetDescRec**前の一覧に表示されているタスクを実行する適切な型で使用できます。 詳細については、次を参照してください。 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)します。
