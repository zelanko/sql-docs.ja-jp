---
title: 引数値のチェック |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b3e4c8772a8d6a6b2a00f6c8ffe4ab610d0e1ec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="argument-value-checks"></a>引数値のチェック
ドライバー マネージャーでは、次の種類の引数を確認します。 特に記載のない限り、ドライバー マネージャーは、引数の値にエラー SQL_ERROR を返します。  
  
-   通常環境、接続、およびステートメントのハンドルは、null ポインターをすることはできません。 ドライバー マネージャーでは、null ハンドルが見つかる場合、SQL_INVALID_HANDLE が返されます。  
  
-   必須のポインター引数がなど*OutputHandlePtr*で**SQLAllocHandle**と*カーソル名*で**SQLSetCursorName**、することはできませんnull ポインターです。  
  
-   ドライバー固有の値をサポートしないオプションのフラグは、有効な値にする必要があります。 たとえば、*操作*で**SQLSetPos** SQL_POSITION、SQL_REFRESH、SQL_UPDATE、SQL_DELETE、または SQL_ADD にする必要があります。  
  
-   ODBC ドライバーでサポートされているのバージョンでは、オプション フラグをサポートする必要があります。 たとえば、*情報の種類*で**SQLGetInfo** SQL_ASYNC_MODE (ODBC 3.0 で導入) をすることはできません、ODBC 2.0 のドライバーを呼び出すときにします。  
  
-   列とパラメーターの番号より大きいまたは 0 で、関数によって 0 より大きい値にする必要があります。 ドライバーは、現在の結果セットまたは SQL ステートメントに基づくこれらの引数値の数の上限をチェックする必要があります。  
  
-   長さ/インジケーター引数とデータのバッファー長の引数は、適切な値を含める必要があります。 内のテーブル名の長さを指定する引数など、 **SQLColumns** (*NameLength3*) SQL_NTS または値より大きくなければなりません 0;*BufferLength*で**SQLDescribeCol** 0 以上にする必要があります。 ドライバーは、これらの引数を確認する必要もあります。 たとえば、その可能性があることを確認*NameLength3*がデータ ソースのテーブル名の最大長未満です。
