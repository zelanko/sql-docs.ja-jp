---
title: "SQLColAttributes (テキスト ファイル ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Text File Driver
ms.assetid: 132fd1c0-1921-4a7d-910e-aedf1bff5453
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f08e06e737466977d81ca3771ae760e1fe1e4334
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlcolattributes-text-file-driver"></a>SQLColAttributes (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
|属性|コメント|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY データ SQL_COLUMN_DISPLAY_SIZE はありません、列の最大長は 2 回、列の最大長です。|  
|SQL_OWNER_NAME|空の文字列 ("") の所有者名がサポートされていないために、この列で返されます。|  
|SQL_QUALIFIER_NAME|ディレクトリへのパスが返されます。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY および LONGVARCHAR 列は、SQL_UNSEARCHABLE として報告されます。<br /><br /> 固定長および可変長のバイナリ、および文字データ型は LONGVARBINARY と LONGVARCHAR がない場合でも、検索可能です。|
