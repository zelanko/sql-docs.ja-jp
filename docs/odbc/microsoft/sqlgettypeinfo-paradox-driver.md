---
title: SQLGetTypeInfo (Paradox ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c212584972f4a7e329d124cc8512be3b1f7a6b9d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898615"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLGetTypeInfo**によって生成されるテーブルに返される型の名前 (TYPE_NAME) は、データソースで最もよく使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKE は、Byte、Counter、Double、Single、Long、Short の各データ型の検索可能な列に返されます。 (LIKE 機能は、ODBC 正規変換関数を使用して値を文字に変換してから、比較を実行することで実現できます)。
