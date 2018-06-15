---
title: SQL_ARD_TYPE |Microsoft ドキュメント
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e3d3ba38947babc5e7335fd38a63db18943b31f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907147"
---
# <a name="sqlardtype"></a>SQL_ARD_TYPE
SQL_ARD_TYPE 型識別子は、バッファー内のデータが、ARD の SQL_DESC_CONCISE_TYPE フィールドに指定された型になることを示すために使用されます。 SQL_ARD_TYPE が入力されて、 *TargetType*への呼び出しの引数**SQLGetData**特定のデータ型と記述子を変更することによって、データを変更するアプリケーションが入力バッファーの有効ではなくフィールドです。 この値のデータ型を結び付ける、  *\*TargetValuePtr*記述子フィールドをバッファーします。 (SQL_ARD_TYPE がへの呼び出しで入力されていない**SQLBindCol**または**SQLBindParameter**バインドされたバッファーの種類が既に SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE フィールドに関連付けられている変更できますいつでもこれらのフィールドのいずれかを変更することによってです。)  
  
 先頭の有効桁数と interval データ型の秒の有効桁数の既定以外の値を指定する SQL_ARD_TYPE 型識別子を使用でき、SQL_C_NUMERIC データの有効桁数と小数点以下桁数の値を入力します。 詳細については、次を参照してください。[先頭既定をオーバーライドすると Interval データ型の秒の有効桁数](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)と[をオーバーライドする既定の有効桁数と小数点以下桁数の数値データ型の](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)、後の「します。
