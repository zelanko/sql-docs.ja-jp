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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72313e0269c93bca9cb2561d89604c3c88c8567b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304803"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro フィールドのデータ型
次の表に、ALTER TABLE と CREATE TABLE の*FieldType*引数の値を示し、 *Nfieldwidth*引数と*nprecision*引数が必要かどうかを示します。  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|説明|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|幅*n*の文字フィールド|  
|D|-|-|日付|  
|F|N|d|*小数点以下を*含む幅*n*の浮動小数点数値フィールド|  
|G|-|-|全般|  
|I|-|-|Integer|  
|L|-|-|論理|  
|M|-|-|メモ|  
|N|N|d|*D*小数点以下を含む幅*n*の数値フィールド|  
|T|-|-|DateTime|  
|Y|-|-|通貨|
