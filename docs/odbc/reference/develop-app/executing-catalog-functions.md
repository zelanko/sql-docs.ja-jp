---
title: カタログ関数を実行する |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 854a7e7fe347bb02c59fe1608afd74bf87be6b7b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="executing-catalog-functions"></a>カタログ関数を実行します。
カタログ関数では、結果セットを作成するため、結果セットの生成 – SQL ステートメントを実行すると同じです。 実際には、カタログ関数では、定義済みの SQL ステートメントを実行しているか、ドライバーまたはデータベース管理システムに付属する定義済みのプロシージャを呼び出すことによって実装されます多くの場合。 ほとんど何も結果セットを作成する SQL ステートメントに適用されるは、カタログ関数にも適用されます。 によって返される行の数を制限と同様に、SQL_ATTR_MAX_ROWS ステートメント属性が、カタログ関数によって返される行の数を制限するなど、**選択**ステートメントです。  
  
 カタログ関数を実行するには、アプリケーションは、関数を呼び出すだけです。  
  
 カタログ関数の詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。
