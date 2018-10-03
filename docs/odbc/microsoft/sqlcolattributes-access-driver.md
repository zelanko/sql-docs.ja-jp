---
title: SQLColAttributes (Access ドライバー) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 0fa4de89a1ca617f7955d89e18650b7cf1e0c0c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610391"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (Access ドライバー)
> [!NOTE]  
>  このトピックでは、Access ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
|属性|コメント|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY データ、SQL_COLUMN_DISPLAY_SIZE は 2 時間列の最大長いない列の最大長です。|  
|SQL_OWNER_NAME|空の文字列 ("") の所有者名がサポートされていないために、この列に返されます。|  
|SQL_QUALIFIER_NAME|データベース ファイルへのパスが返されます。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY および LONGVARCHAR 列は、SQL_UNSEARCHABLE として報告されます。<br /><br /> 固定長および可変長のバイナリおよび文字データ型は LONGVARBINARY および LONGVARCHAR がない場合でも、検索可能です。|  
  
> [!NOTE]  
>  上記はによって返される属性の完全な一覧ではない**SQLColAttributes**します。
