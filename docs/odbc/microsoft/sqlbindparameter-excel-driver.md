---
title: SQLBindParameter (Excel ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8b33200e0628566bc88f770ca1fe8fd895ecbf2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063250"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 Microsoft Excel driver が使用されている場合、パラメーターを使用して SQL_CHAR 列に NULL を挿入する INSERT ステートメントを実行すると、SQLSTATE 01004 の "データが切り捨てられました" という SQL_SUCCESS_WITH_INFO が返されます。
