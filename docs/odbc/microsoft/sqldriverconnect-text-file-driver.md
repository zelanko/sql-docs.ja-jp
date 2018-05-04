---
title: SQLDriverConnect (テキスト ファイル ドライバー) |Microsoft ドキュメント
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
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 597c27d1f0e1fe39f8226f20b56bddb1036f6311
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
