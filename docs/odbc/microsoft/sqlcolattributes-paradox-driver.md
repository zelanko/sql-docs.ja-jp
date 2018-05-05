---
title: SQLColAttributes (Paradox ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLColAttributes
ms.assetid: bbeef024-d470-4d28-b61b-26997ef41007
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91ac34f1b5ca6192dfd01176c6fd099aa5f22689
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolattributes-paradox-driver"></a>SQLColAttributes (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
|属性|コメント|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY データ SQL_COLUMN_DISPLAY_SIZE はありません、列の最大長は 2 回、列の最大長です。|  
|SQL_OWNER_NAME|空の文字列 ("") の所有者名がサポートされていないために、この列で返されます。|  
|SQL_QUALIFIER_NAME|ディレクトリへのパスが返されます。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY および LONGVARCHAR 列は、SQL_UNSEARCHABLE として報告されます。<br /><br /> 固定長および可変長のバイナリ、および文字データ型は LONGVARBINARY と LONGVARCHAR がない場合でも、検索可能です。|  
  
> [!NOTE]  
>  上記はによって返される属性の完全な一覧ではない**SQLColAttributes**です。
