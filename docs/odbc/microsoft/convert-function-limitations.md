---
title: 関数の制限の変換 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, CONVERT function limitations
- Convert function limitations [ODBC]
ms.assetid: 3c81fc58-57f0-4dd7-be16-2b146eb15cbc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65cc8fa7517d3093b7314cacdafd8f607d89bc3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081995"
---
# <a name="convert-function-limitations"></a>CONVERT 関数の制限事項
型変換エラーが発生すると、影響を受ける列が NULL に設定されます。  
  
 DATE も TIMESTAMP データ型も、CONVERT 関数によって別のデータ型 (またはそれ自体) に変換することはできません。
