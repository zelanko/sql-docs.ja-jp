---
title: 場所句の制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e883d585db0fe11e92b188b2cfc26db9fff415fe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057773"
---
# <a name="where-clause-limitations"></a>WHERE 句の制限事項
WHERE 句内の句の最大数は、40 です。  
  
 LONGVARBINARY および LONGVARCHAR 列で、最大 255 文字のリテラルと比較することができますが、パラメーターを使用して比較することはできません。
