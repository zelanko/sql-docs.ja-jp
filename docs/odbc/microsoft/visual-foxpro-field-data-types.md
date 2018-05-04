---
title: Visual FoxPro フィールド データの種類 |Microsoft ドキュメント
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
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf6df134c5a4ad54e574e42e57d7a68e10b4e077
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
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
