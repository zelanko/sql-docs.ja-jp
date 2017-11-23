---
title: "SQLDriverConnect (Excel ドライバー) |Microsoft ドキュメント"
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
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3db750232c45ce02b1dfe32e103d35ab20b366c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバーに固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成せずに、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列で、次のキーワードはサポートされて: **DSN**、 **DBQ**、および**FIL**です。  
  
 次の表は、各ドライバーへの接続に必要な最小のキーワードを示しています、併用キーワード/値ペアの例を示します**SQLDriverConnect**です。 DRIVERID 値の一覧については、次を参照してください。 [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。  
  
> [!NOTE]  
>  DBQ または DefaultDir が指定されていない場合、Microsoft Excel 3.0 または 4.0 ドライバー、ドライバーは、現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|3.0 または 4.0、Microsoft Excel|ドライバー、DriverID|ドライバー {Excel ドライバー (*.xls)} を = です。DBQ = c:\temp です。DriverID 278 を =|  
|Microsoft Excel 5.0 または 7.0|ドライバー、DriverID、DBQ|ドライバー {Excel ドライバー (*.xls)} を = です。DBQ=c:\temp\sample.xls です。DriverID 22 を =|  
|Microsoft Excel 97 以降|ドライバー、DriverID、DBQ|ドライバー {Excel ドライバー (*.xls)} を = です。DBQ=c:\temp\sample.xls です。DriverID 790 を =|
