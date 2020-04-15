---
title: メタデータの使用方法 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 70fb976c-9342-4edd-b066-1140696fd0fa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbbba96fa2e99a2ccc0618f31e3b29e7d479f703
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300172"
---
# <a name="how-is-metadata-used"></a>メタデータの使用方法
アプリケーションは、ほとんどの結果セット操作にメタデータを必要とします。 たとえば、列のデータ型を使用して、列にバインドされている変数の種類を判断します。 この例では、文字列のバイト長を使用して、その列のデータを表示するのに必要なスペースの量を決定します。 アプリケーションが列のメタデータを判断する方法は、アプリケーションの種類によって異なります。  
  
 垂直アプリケーションは、定義済みのテーブルを処理し、それらのテーブルに対して定義済みの操作を実行します。 このようなアプリケーションの結果セットメタデータは、アプリケーションが書き込まれる前に定義され、アプリケーション開発者によって制御されるため、アプリケーションにハードコーディングできます。 たとえば、データ ソース内で受注 ID 列が 4 バイト integer 型で定義されている場合、アプリケーションは常に 4 バイト integer をこの列にバインドできます。 メタデータがアプリケーション内でハードコーディングされている場合、アプリケーションが使用するテーブルへの変更は、通常、アプリケーション コードに対する変更になります。 このような変更は通常、アプリケーションの新しいリリースの一部として行われるため、これはめったに問題ではありません。  
  
 垂直アプリケーションと同様に、カスタムアプリケーションは一般に定義済みテーブルを操作し、それらのテーブルに対して事前定義された操作を実行します。 たとえば、アプリケーションが 3 つの異なるデータ ソース間でデータを転送するように記述される場合があります。転送されるデータは、通常、アプリケーションが書き込まれるときに認識されます。 したがって、カスタム アプリケーションにも、ハードコーディングされたメタデータが含まれます。  
  
 汎用アプリケーション、特にアドホック クエリをサポートするアプリケーションは、作成する結果セットのメタデータをほとんど知りません。 したがって、次のセクション[「SQLDescribeCol と SQLColAttribute」](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)で説明されている関数**SQLNumResultCols** **、SQLDescribeCol、** および**SQLColAttribute**を使用して、実行時にメタデータを検出する必要があります。  
  
 すべてのアプリケーションは、その種類に関係なく、カタログ関数によって返される結果セットのメタデータをハードコーディングできます。 これらの結果セットは、このマニュアルの参照セクションで定義されています。
