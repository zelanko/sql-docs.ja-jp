---
title: SQLColAttributes (Access Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c78229da8a577670ba31ae82c679bfefbef4f80
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67903981"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (Access ドライバー)
> [!NOTE]  
>  このトピックでは、ドライバー固有の情報にアクセスします。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|Attribute|説明|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY データの場合、SQL_COLUMN_DISPLAY_SIZE は列の最大長であり、列の最大長では2ではありません。|  
|SQL_OWNER_NAME|この列には、所有者名がサポートされていないため、空の文字列 ("") が返されます。|  
|SQL_QUALIFIER_NAME|データベースファイルへのパスが返されます。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY および LONGVARBINARY 列は SQL_UNSEARCHABLE として報告されます。<br /><br /> 固定長と可変長のバイナリおよび文字データ型は、LONGVARBINARY と LONGVARBINARY がない場合でも検索できます。|  
  
> [!NOTE]  
>  上記は、 **Sqlcolattributes**によって返される属性の完全な一覧ではありません。
