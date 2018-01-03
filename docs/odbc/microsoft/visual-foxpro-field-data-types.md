---
title: "Visual FoxPro フィールド データの種類 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c99a094c690882c6f2877964ae19b335cff1509
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro フィールドのデータ型
次の表に、値を*FieldType* ALTER TABLE と CREATE TABLE で引数を示し、かどうか*nFieldWidth*と*nPrecision*引数必須。  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|c|×|-|幅の文字のフィールド*n*|  
|D|-|-|date|  
|F|×|d|数値フィールドの幅を浮動 *n* で*d*小数点以下桁数|  
|G|-|-|全般|  
|I|-|-|Integer|  
|L|-|-|論理|  
|M|-|-|メモ|  
|×|×|d|数値フィールドの幅の *n* で*d*小数点以下桁数|  
|T|-|-|DateTime|  
|Y|-|-|通貨|
