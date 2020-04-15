---
title: ビジュアル FoxPro フィールド データ型 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304803"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro フィールドのデータ型
次の表は、ALTER TABLE および CREATE TABLE の*FieldType*引数の値を示し *、nFieldWidth*引数と*nPrecision*引数が必要かどうかを示します。  
  
|*Fieldtype*|*フィールド幅*|*n精密*|説明|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|幅*n*の文字フィールド|  
|D|-|-|Date|  
|F|N|d|d*小数*位の幅*n*の浮動小数点数値フィールド|  
|G|-|-|全般|  
|I|-|-|Integer|  
|L|-|-|論理|  
|M|-|-|メモ|  
|N|N|d|幅 n*の*数値フィールド (*小数点以下の桁数が d)*|  
|T|-|-|DateTime|  
|Y|-|-|Currency|
