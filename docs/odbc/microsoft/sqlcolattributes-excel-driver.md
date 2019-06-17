---
title: SQLColAttributes (Excel ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 67ba6df9955a1b138ebb919d410ef7817e1fb48e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666274"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
|属性|コメント|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY データ、SQL_COLUMN_DISPLAY_SIZE は 2 時間列の最大長いない列の最大長です。|  
|SQL_OWNER_NAME|空の文字列 ("") の所有者名がサポートされていないために、この列に返されます。|  
|SQL_QUALIFIER_NAME|ディレクトリへのパスが返されます。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY および LONGVARCHAR 列は、SQL_UNSEARCHABLE として報告されます。<br /><br /> 固定長および可変長のバイナリおよび文字データ型は LONGVARBINARY および LONGVARCHAR がない場合でも、検索可能です。|  
  
> [!NOTE]  
>  上記はによって返される属性の完全な一覧ではない**SQLColAttributes**します。
