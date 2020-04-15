---
title: SQL 記述と SQL コーラ属性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], and SQLDescribeCol
- SQLDescribeCol function [ODBC], and SQLColAttribute
- result sets [ODBC], metadata
- retrieving result set meta data [ODBC]
- metadata [ODBC], result set
ms.assetid: c2ca442c-03a8-4e0f-9e67-b300bb15962f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8bd21010908473e4216a02a504b2de25578d5c84
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299762"
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol および SQLColAttribute
**SQLDescribeCol**結果セットのメタデータを取得**するために使用されます**。 これら 2 つの関数の違いは **、SQLDescribeCol**は常に同じ 5 つの情報 (列名、データ型、精度、小数点以下桁数、および NULL 値の許容可能性) を返し **、SQLColAttribute**はアプリケーションから要求された単一の情報を返す点です。 ただし **、SQLColAttribute**は、列の大文字と小文字の区別、表示サイズ、更新可能性、検索可能性など、より豊富なメタデータを返すことができます。  
  
 多くのアプリケーション 、特にデータを表示するだけのアプリケーションでは **、SQLDescribeCol**によって返されるメタデータのみが必要です。 これらのアプリケーションでは、情報が 1 回の呼び出しで返されるため **、SQLCol 属性**よりも**SQLDescribeCol**を使用する方が高速です。 他のアプリケーション、特にデータを更新するアプリケーションでは **、SQLColAttribute**によって返される追加のメタデータが必要であるため、両方の関数が使用されます。 さらに **、SQLColAttribute**は、ドライバー固有のメタデータをサポートします。詳細については、「[ドライバ固有のデータ型、記述子の型、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)」を参照してください。  
  
 アプリケーションは、ステートメントの準備または実行後、および結果セット上のカーソルが閉じられる前に、いつでも結果セットのメタデータを取得できます。 ステートメントの準備後、実行前に結果セットのメタデータを必要とするアプリケーションはほとんどありません。 可能であれば、一部のデータ ソースは準備済みステートメントのメタデータを返すことができず、ドライバーでこの機能をエミュレートするプロセスが遅い場合があるため、アプリケーションはステートメントの実行後までメタデータの取得を待機する必要があります。 たとえば、ドライバーは **、SELECT**ステートメントの**WHERE**句を**WHERE 1 = 2**句に置き換え、結果のステートメントを実行することで、ゼロ行の結果セットを生成できます。  
  
 メタデータは、データ ソースから取得する際に多くの場合、コストがかかります。 このため、ドライバーは、サーバーから取得したメタデータをキャッシュし、結果セット上のカーソルが開いている間、それを保持する必要があります。 また、アプリケーションは絶対に必要なメタデータのみを要求する必要があります。
