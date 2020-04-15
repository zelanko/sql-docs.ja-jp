---
title: カタログ関数の実行 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6469a5394e232ab9d9135fbbbd56ba7b791ccbcb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305723"
---
# <a name="executing-catalog-functions"></a>カタログ関数の実行
カタログ関数は結果セットを作成するため、結果セット生成 SQL ステートメントを実行するのと同じです。 実際、カタログ関数は、多くの場合、定義済みの SQL ステートメントを実行するか、ドライバーまたは DBMS に付属する定義済みのプロシージャを呼び出すことによって実装されます。 結果セットを作成する SQL ステートメントに適用されるほとんどすべてのものは、カタログ関数にも適用されます。 たとえば、SQL_ATTR_MAX_ROWSステートメント属性は **、SELECT ステートメント**によって返される行数を制限するのと同様に、カタログ関数から返される行数を制限します。  
  
 カタログ関数を実行するには、アプリケーションは関数を呼び出すだけです。  
  
 カタログ関数の詳細については、[カタログ](../../../odbc/reference/develop-app/catalog-functions.md)関数を参照してください。
