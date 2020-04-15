---
title: SQL_ARD_TYPE |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7e28d6babb7db8364697ae62092256396b44914
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305033"
---
# <a name="sql_ard_type"></a>SQL_ARD_TYPE
SQL_ARD_TYPE型識別子は、バッファー内のデータが ARD のSQL_DESC_CONCISE_TYPE フィールドで指定された型であることを示すために使用されます。 SQL_ARD_TYPEは、特定のデータ型ではなく**SQLGetData**の呼び出しの*TargetType*引数に入力され、アプリケーションは記述子フィールドを変更することによってバッファーのデータ型を変更できます。 この値は、記述子フィールドに*\*、ターゲット値Ptr*バッファーのデータ型を結び付けます。 (バインドされたバッファーの型は既にSQL_DESC_TYPEおよびSQL_DESC_CONCISE_TYPE フィールドに関連付けられており、これらのフィールドのいずれかを変更することでいつでも変更できるため **、SQLBindCol**または**SQLBindParameter**の呼び出しではSQL_ARD_TYPEが入力されません。  
  
 SQL_ARD_TYPE型識別子を使用すると、間隔データ型の先行精度と秒精度、およびSQL_C_NUMERICデータ型の精度とスケール値に対して、デフォルト以外の値を指定できます。 詳細については、この付録の「[間隔データ型の既定の先行精度と秒精度のオーバーライド](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)」および「[数値データ型の既定の精度と小数点以下桁数のオーバーライド](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)」を参照してください。
