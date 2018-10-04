---
title: SQLDriverConnect (Access ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a71874c91e48c25072fbfed8f66a312d65b4697
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626386"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access ドライバー)
> [!NOTE]  
>  このトピックでは、Access ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成することがなく、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列では、次のキーワードがサポートされて: **DSN**、 **DBQ**、および**FIL**します。  
  
 **UID**と**PWD**キーワードもサポートされています。  
  
 PWD キーワードの特殊文字含める必要がありますいない (SQL_SPECIAL_CHARACTERS でを参照してください。 **SQLGetInfo**に返される値)。  
  
 次の表は、各ドライバーでは、接続に必要な最小のキーワードを示しています。 と併用キーワード/値ペアの例を示します**SQLDriverConnect**します。 DRIVERID 値の一覧については、次を参照してください。 [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|Microsoft Access|ドライバー、DBQ|ドライバー {0} Microsoft Access ドライバー (*.mdb)} を = です。DBQ = c:\\\temp\\\sample.mdb|
