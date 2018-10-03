---
title: SQLDescribeCol および SQLColAttribute |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e569e51540cbaa5612b158abdacac5faae77f940
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722630"
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol および SQLColAttribute
**SQLDescribeCol**と**SQLColAttribute**結果セットのメタデータの取得に使用されます。 これら 2 つの関数の違いは**SQLDescribeCol**同じの 5 つの中の情報 (列の名前、データ型、有効桁数、スケール、および null 値許容属性) は常に返します**SQLColAttribute** 、単一のアプリケーションによって要求された情報を返します。 ただし、 **SQLColAttribute**列の大文字小文字の区別を含む、メタデータの豊富な機能の選択範囲を返す、サイズ、更新、および検索機能を表示できます。  
  
 特に、データのみが表示される、多くのアプリケーションによって返されるメタデータのみを必要と**SQLDescribeCol**します。 これらのアプリケーションが高速化を使用する**SQLDescribeCol**より**SQLColAttribute**情報が 1 回の呼び出しで返されるためです。 特に、データを更新する他のアプリケーションによって返される追加のメタデータを必要と**SQLColAttribute**のため両方の関数を使用します。 さらに、 **SQLColAttribute**ドライバー固有のメタデータをサポートしています。 詳細については、次を参照してください。[ドライバー固有のデータ型、記述子の種類、情報の種類、診断型、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)します。  
  
 アプリケーションでは、結果の上にカーソルを前にセットが閉じられると、ステートメントが準備または実行後、いつでも、結果セットのメタデータを取得できます。 ほとんどのアプリケーションでは、ステートメントが準備された後、実行される前に結果セットのメタデータが必要 します。 可能であれば、アプリケーションは、メタデータを取得するまで一部のデータ ソースは、準備されたステートメント用のメタデータを返すことはできませんし、多くの場合、低速な処理は、ドライバーでは、この機能をエミュレートするため、ステートメントが実行された後に待機する必要があります。 など、ドライバーは置き換えることにより、0 行の結果を生成する可能性があります、**場所**の句、**選択**ステートメントと句**場所 1 = 2**を実行して、結果として得られるステートメント。  
  
 メタデータは、データ ソースから取得する高価な多くの場合。 このため、ドライバーは、サーバーから取得するメタデータの結果の上にカーソルが設定されている限り開いている保持をキャッシュする必要があります。 また、アプリケーションでは、絶対に必要なメタデータのみを要求する必要があります。
