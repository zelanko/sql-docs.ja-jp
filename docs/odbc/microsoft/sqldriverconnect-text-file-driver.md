---
title: "SQLDriverConnect (テキスト ファイル ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 117b619b351e5a8c1e2c0865fe0ed6add5589ecb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成せずに、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列で、次のキーワードはサポートされて: **DSN**、 **DBQ**、および**FIL**です。  
  
 次の表は、各ドライバーへの接続に必要な最小のキーワードを示しています、併用キーワード/値ペアの例を示します**SQLDriverConnect**です。 DRIVERID 値の一覧については、次を参照してください。 [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。  
  
> [!NOTE]  
>  テキストのドライバー、DBQ または DefaultDir が指定されていない場合、ドライバーは、現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|テキスト|Driver|ドライバー = {Microsoft Text Driver (*.txt;\*です。csv)} です。DefaultDir c:\temp を =|
