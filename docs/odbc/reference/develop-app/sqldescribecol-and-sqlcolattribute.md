---
title: "SQLDescribeCol と SQLColAttribute |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLColAttribute function [ODBC], and SQLDescribeCol
- SQLDescribeCol function [ODBC], and SQLColAttribute
- result sets [ODBC], metadata
- retrieving result set meta data [ODBC]
- metadata [ODBC], result set
ms.assetid: c2ca442c-03a8-4e0f-9e67-b300bb15962f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a80ccf6ed695433a109770a567f50d100fd3a33
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol と SQLColAttribute
**SQLDescribeCol**と**SQLColAttribute**結果セットのメタデータの取得に使用されます。 これら 2 つの関数の違いを**SQLDescribeCol**中に情報 (列の名前、データ型、有効桁数、スケール、および null 値許容属性) の同じ 5 つの部分は常に返します**SQLColAttribute** 、1 つのアプリケーションによって要求された情報を返します。 ただし、 **SQLColAttribute**列の大文字小文字の区別を含む、メタデータのはるかに充実した選択範囲を返す、サイズ、更新、および検索機能を表示できます。  
  
 によって返されるメタデータのみ必要です。 特に、データのみが表示される多くのアプリケーション**SQLDescribeCol**です。 これらのアプリケーションをすばやく使用**SQLDescribeCol**より**SQLColAttribute**情報が 1 回の呼び出しで返されるためです。 特に、データを更新する、他のアプリケーションによって返される追加のメタデータを必要と**SQLColAttribute**どちらの関数を使用します。 さらに、 **SQLColAttribute**ドライバー固有のメタデータをサポートしています。 詳細については、次を参照してください。[ドライバー固有のデータ型、記述子の種類、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)です。  
  
 アプリケーションでは、結果の上にカーソルの前にセットが閉じられると、ステートメントが準備または実行後に結果セットのメタデータを取得できます。 ほとんどのアプリケーションでは、ステートメントが準備された後が実行される前に結果セットのメタデータが必要です。 可能であれば、アプリケーションは、メタデータを取得するまで、ステートメントの実行後に、一部のデータ ソースは、準備されたステートメント用のメタデータを返すことはできませんし、多くの場合、低速な処理では、ドライバーでこの機能をエミュレートするため待機する必要があります。 など、ドライバーは置き換えることにより、0 行の結果を生成する可能性があります、**場所**の句、**選択**ステートメントと句**場所 1 = 2**を実行して、結果として得られるステートメントです。  
  
 メタデータは、データ ソースから取得する高価な多くの場合。 このため、ドライバーは、サーバーから取得し、保持の結果上にカーソルが設定されている限りが開いているすべてのメタデータをキャッシュする必要があります。 また、アプリケーションでは、絶対に必要なメタデータのみを要求する必要があります。

