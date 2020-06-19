---
title: 数値データ形式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- integer data types [Integration Services]
- numeric data formats for fast parse
- locale-sensitive parsing [Integration Services]
- fast parse [Integration Services]
ms.assetid: fa3975ce-9d21-408a-857d-f85e30af27b0
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 1f9e37d3062bba763f44e0eef14b216972b29f1d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965112"
---
# <a name="numeric-data-formats"></a>数値データ形式
  高速解析は、データを解析するための、高速で単純なロケール非依存型のルーチンのセットです。 高速解析でサポートされているデータ型は、整数データ型の限定された形式のセットのみです。  
  
## <a name="integer-data-types"></a>整数データ型  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で用意されている整数データ型は、DT_I1、DT_UI1、DT_I2、DT_UI2、DT_I4、DT_UI4、DT_I8、および DT_UI8 です。 詳細については、「 [Integration Services データ型](data-flow/integration-services-data-types.md)」を参照してください。  
  
 高速解析では、次の形式の整数データ型がサポートされています。  
  
-   0 以上の先頭および末尾のスペース、またはタブ ストップ。 たとえば、値 "  123  " は有効です。 値がすべてスペースの場合は、0 に評価されます。  
  
-   先頭の正符号、負符号、または符号なし。 たとえば、値 +123、-123、および 123 は有効です。  
  
-   1 つ以上のアラビア数字 (0 ～ 9)。 たとえば、値 345 は有効です。 他の言語の数値はサポートされません。  
  
 次の形式を含むデータ形式はサポートされません。  
  
-   特殊文字。 たとえば、通貨文字 $ はサポートされないため、値 $20 は解析できません。  
  
-   ライン フィード、キャリッジ リターン、改行なしスペースなどの空白文字。 たとえば、値 " 123" は解析できません。  
  
-   整数の 16 進表記。 たとえば、値 2EE は解析できません。  
  
-   整数の科学的表記法。 たとえば、値 1E+10 は解析できません。  
  
 次の形式は、整数の出力データ形式です。  
  
-   負の数値を表す負符号、および正の数値を表す符号なし。  
  
-   空白なし。  
  
-   1 つ以上のアラビア数字 (0 ～ 9)。  
  
  
