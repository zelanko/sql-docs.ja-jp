---
title: SQLColAttributes (Excel Driver) |Microsoft Docs
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
ms.openlocfilehash: cd3076ba19b9f5372074a9256e20d73858f69c09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132671"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|Attribute|説明|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY データの場合、SQL_COLUMN_DISPLAY_SIZE は列の最大長であり、列の最大長では2ではありません。|  
|SQL_OWNER_NAME|この列には、所有者名がサポートされていないため、空の文字列 ("") が返されます。|  
|SQL_QUALIFIER_NAME|ディレクトリへのパスが返されます。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY および LONGVARBINARY 列は SQL_UNSEARCHABLE として報告されます。<br /><br /> 固定長と可変長のバイナリおよび文字データ型は、LONGVARBINARY と LONGVARBINARY がない場合でも検索できます。|  
  
> [!NOTE]  
>  上記は、 **Sqlcolattributes**によって返される属性の完全な一覧ではありません。
