---
title: SQLDriverConnect (Paradox ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bae4a842729c8d302731ebf5fec22abb817f4c75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654760"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成することがなく、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列では、次のキーワードがサポートされて: **DSN**、 **DBQ**、および**FIL**します。  
  
 **PWD**キーワードもサポートされます。 PWD キーワードの特殊文字含める必要がありますいない (SQL_SPECIAL_CHARACTERS でを参照してください。 **SQLGetInfo**に返される値)。  
  
 パスワードで保護されたファイルを開いた後にユーザーが、他のユーザーは同じファイルを開くには使用できません。  
  
 次の表は、各ドライバーでは、接続に必要な最小のキーワードを示しています。 と併用キーワード/値ペアの例を示します**SQLDriverConnect**します。 DRIVERID 値の一覧については、[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)を参照してください。  
  
> [!NOTE]  
>  Paradox ドライバー、DBQ または DefaultDir が指定されていない場合、ドライバーは、現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|例|  
|------------|-----------------------|-------------|  
|Paradox|ドライバー、DriverID|ドライバー {0} Microsoft Paradox ドライバー (*.db)} を = です。DBQ = c:\temp; DriverID = 26|
