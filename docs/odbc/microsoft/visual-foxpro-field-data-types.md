---
title: Visual FoxPro フィールドのデータ型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07aa06eae9f1e75a047bdd302754d884790436e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806125"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro フィールドのデータ型
次の表の値、 *FieldType* ALTER TABLE と CREATE TABLE で引数を示し、かどうか*nFieldWidth*と*nPrecision*引数必須。  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|説明|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|c|N|-|文字のフィールドの幅の*n*|  
|D|-|-|date|  
|F|N|d|数値フィールドの幅を浮動*n*で*d*小数点以下桁数|  
|G|-|-|全般|  
|I|-|-|Integer|  
|L|-|-|論理|  
|M|-|-|メモ|  
|N|N|d|数値フィールドの幅の*n*で*d*小数点以下桁数|  
|T|-|-|DateTime|  
|Y|-|-|通貨|
