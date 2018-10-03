---
title: カタログ関数の実行 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: daf1ab2fc05b198e71b45cb02b4577eebee5c5b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704290"
---
# <a name="executing-catalog-functions"></a>カタログ関数の実行
カタログ関数では、結果セットを作成するため、結果セットの生成 – SQL ステートメントを実行すると同じです。 実際には、カタログ関数は定義済みの SQL ステートメントを実行またはドライバーまたは DBMS に同梱されている定義済みのプロシージャを呼び出すことによって多くの場合、実装されます。 結果セットを作成する SQL ステートメントに適用するほぼあらゆる操作は、カタログ関数にも適用されます。 によって返される行の数を制限と同じように、この SQL_ATTR_MAX_ROWS ステートメント属性が、カタログ関数によって返される行の数を制限するなど、**選択**ステートメント。  
  
 カタログ関数を実行するには、アプリケーションはでは、関数を呼び出します。  
  
 カタログ関数の詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)します。
