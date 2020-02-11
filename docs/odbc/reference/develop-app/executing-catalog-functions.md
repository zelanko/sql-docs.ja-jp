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
ms.openlocfilehash: ab6eba9c4a3df3e16e35d8a93dc95209a093fb80
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901271"
---
# <a name="executing-catalog-functions"></a>カタログ関数の実行
カタログ関数は結果セットを作成するので、結果セット生成の SQL ステートメントを実行するのと同じです。 実際、カタログ関数は、定義済みの SQL ステートメントを実行したり、ドライバーまたは DBMS に付属する定義済みプロシージャを呼び出したりすることによって実装されます。 結果セットを作成する SQL ステートメントに適用されるほとんどすべての処理は、カタログ関数にも適用されます。 たとえば、SQL_ATTR_MAX_ROWS statement 属性では、 **SELECT**ステートメントによって返される行の数を制限するのと同じように、カタログ関数によって返される行の数が制限されます。  
  
 カタログ関数を実行するために、アプリケーションは関数を呼び出します。  
  
 カタログ関数の詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。
