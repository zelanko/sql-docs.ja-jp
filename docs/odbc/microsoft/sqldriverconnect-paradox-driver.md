---
title: SQLDriverConnect (Paradox ドライバー) |Microsoft ドキュメント
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
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f34d1cd8d17c077a4879cf8dd39331533e3b0c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成せずに、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列で、次のキーワードはサポートされて: **DSN**、 **DBQ**、および**FIL**です。  
  
 **PWD**キーワードもサポートします。 PWD キーワードを含めないでくださいの特殊文字 (で SQL_SPECIAL_CHARACTERS を参照してください**SQLGetInfo**返された値)。  
  
 パスワードで保護されたファイルを開いた後に、ユーザーが、他のユーザーは、同じファイルを開くには使用できません。  
  
 次の表は、各ドライバーへの接続に必要な最小のキーワードを示しています、併用キーワード/値ペアの例を示します**SQLDriverConnect**です。 DRIVERID 値の一覧については、次を参照してください。 [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。  
  
> [!NOTE]  
>  Paradox ドライバー、DBQ または DefaultDir が指定されていない場合、ドライバーは、現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|例|  
|------------|-----------------------|-------------|  
|Paradox|ドライバー、DriverID|ドライバー {Microsoft Paradox ドライバー (*.db)} を = です。DBQ = c:\temp; DriverID 26 を =|
