---
title: Visual FoxPro フィールド データの種類 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2bb370e2e27d2c058b93bbe25024b33947994d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro フィールドのデータ型
次の表に、値を*FieldType* ALTER TABLE と CREATE TABLE で引数を示し、かどうか*nFieldWidth*と*nPrecision*引数必須。  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|×|-|幅の文字フィールド*n*|  
|D|-|-|日付|  
|F|×|d|数値フィールドの幅を浮動*n*で*d*小数点以下桁数|  
|G|-|-|全般|  
|I|-|-|Integer|  
|L|-|-|論理|  
|M|-|-|メモ|  
|×|×|d|数値フィールドの幅の*n*で*d*小数点以下桁数|  
|T|-|-|DateTime|  
|Y|-|-|通貨|
