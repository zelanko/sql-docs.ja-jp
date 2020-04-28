---
title: SQLProcedureColumns (Access Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be17776ac6b6879140a7c57bede1b3cb539d97be
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299462"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (Access ドライバー)
> [!NOTE]  
>  このトピックでは、ドライバー固有の情報にアクセスします。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 アプリケーション開発者は、ドライバー定義の列を検索し、結果セットの末尾から逆方向に進む必要があります。  
  
|列|説明|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT または SQL_RESULT_COL|  
|数値|これは、結果セットの末尾に返されるドライバー固有の列です。 列の SQL 型は整数です。|
