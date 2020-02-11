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
ms.openlocfilehash: 217058bf328677bf375d346ae7201c6eb81efa4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087955"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro フィールドのデータ型
次の表に、ALTER TABLE と CREATE TABLE の*FieldType*引数の値を示し、 *Nfieldwidth*引数と*nprecision*引数が必要かどうかを示します。  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|[説明]|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|DOUBLE|  
|C|N|-|幅*n*の文字フィールド|  
|D|-|-|Date|  
|F|N|d|*小数点以下を*含む幅*n*の浮動小数点数値フィールド|  
|G|-|-|全般|  
|I|-|-|整数|  
|L|-|-|論理|  
|M|-|-|メモ|  
|N|N|d|*D*小数点以下を含む幅*n*の数値フィールド|  
|T|-|-|DateTime|  
|Y|-|-|Currency|
