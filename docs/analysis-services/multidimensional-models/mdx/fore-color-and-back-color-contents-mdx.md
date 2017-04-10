---
title: "FORE_COLOR および BACK_COLOR の内容 (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FORE_COLOR の内容"
  - "バックグラウンド [MDX]"
  - "セル [MDX]"
  - "カラー [MDX]"
  - "セル カラー情報の保存"
  - "セル バックグラウンド"
  - "BACK_COLOR の内容"
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# FORE_COLOR および BACK_COLOR の内容 (MDX)
  セル プロパティ **FORE_COLOR** および **BACK_COLOR** は、セルのテキストの色および背景色についての情報を Microsoft Windows オペレーティング システムの赤緑青 (RGB) 形式で格納します。  
  
 通常の RGB 色の有効範囲は 0 ～ 16,777,215 (&H00FFFFFF) です。 この範囲の高位バイトは常に 0 で、最も低いバイトから意味を成すバイトまでの下位 3 バイトによって、赤、緑、および青それぞれの量が決まります。 赤、緑、および青のコンポーネントは、それぞれ 0 ～ 255 (&HFF) までの数値で表されます。  
  
## 参照  
 [セル プロパティの使用 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-cell-properties-mdx.md)  
  
  