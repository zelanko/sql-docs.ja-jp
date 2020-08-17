---
description: SQLGetTypeInfo (Paradox ドライバー)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bedb9170ba18b04e47f9e56bdc47098b9182f8b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339948"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLGetTypeInfo**によって生成されるテーブルに返される型の名前 (TYPE_NAME) は、データソースで最もよく使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKE は、Byte、Counter、Double、Single、Long、Short の各データ型の検索可能な列に返されます。 (LIKE 機能は、ODBC 正規変換関数を使用して値を文字に変換してから、比較を実行することで実現できます)。
