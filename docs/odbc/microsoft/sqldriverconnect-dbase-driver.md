---
title: SQLDriverConnect (dBASE ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e4eeaa7ba710814bfeb8c5b4f5aa0dbd2d30ef7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690882"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成することがなく、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列では、次のキーワードがサポートされて: **DSN**、 **DBQ**、および**FIL**します。  
  
 Paradox ドライバーを使用すると、ユーザーがパスワードで保護されたファイルを開いた後、他のユーザーは同じファイルを開くには許可されません。  
  
 次の表は、各ドライバーでは、接続に必要な最小のキーワードを示しています。 と併用キーワード/値ペアの例を示します**SQLDriverConnect**します。 DRIVERID 値の一覧については、次を参照してください。 [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)します。  
  
> [!NOTE]  
>  DBASEdriver、DBQ または DefaultDir が指定されていない場合、ドライバーは、現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|dBASE|ドライバー、DriverID|ドライバー {0} Microsoft トランスレーター)} を = です。DBQ c:\temp; を =DriverID 277 を =|
