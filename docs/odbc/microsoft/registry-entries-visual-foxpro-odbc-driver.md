---
title: レジストリエントリ (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bd2d419a94c45a872789e095b014159b41d7c217
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304839"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>レジストリ エントリ (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーをインストールすると、インストールプログラムによって、システムのレジストリがレジストリキー HKEY_LOCAL_MACHINE \SOFTWARE\ODBC\ODBCInst.ini に更新され、Microsoft Visual FoxPro Driver という名前の新しいキーが追加されます。 そのキーの下に、次の表で説明する値が追加されます。  
  
|値の名前|値の型|値|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|"YYN"|  
|ドライバー|REG_SZ|Vfpodbc ファイルへのシステムパス|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"* .dbf,\*. cdx,\*. fpt"|  
|FileUsage|REG_SZ|"1"|  
|セットアップ|REG_SZ|Vfpodbc ファイルへのシステムパス|  
|SQLLevel|REG_SZ|"0"|  
  
 また、インストールプログラムは、既定の Visual FoxPro ドライバーを表す "Visual FoxPro ファイル" キーをシステムの HKEY_CURRENT_USER \SOFTWARE\ODBC\Odbc.ini キーに追加します。 このキーの下で、インストールプログラムによって、次の表に示す値が追加されます。  
  
|値の名前|値の型|値|  
|----------------|----------------|-----------|  
|ドライバー|REG_SZ|Vfpodbc ファイルへのシステムパス|  
  
 ODBC 構成に Visual FoxPro ODBC データソースを追加するたびに、そのデータソース名に新しいキーが追加されます。 データソースの値は、次の表に示すように、[ **ODBC Visual FoxPro セットアップ**] ダイアログボックスで設定した値に対応しています。  
  
|値の名前 (キーワード)|値の種類|値|  
|----------------------------|----------------|-----------|  
|[部単位で印刷]|REG_SQ|サポートされている照合順序|  
|説明|REG_SZ|データソースのユーザーの説明|  
|ドライバー||Vfpodbc ファイルへのシステムパス|  
|排他的||はい、いいえ|  
|BackgroundFetch||はい、いいえ|  
|SourceDB|REG_SZ|へのパス。DBC ファイル|  
|SourceType|REG_SZ|"DBC" または "DBF"|  
  
 この情報に直接アクセスすることはできません。レジストリの管理は、データソースを追加、変更、または削除するときに、ODBC 管理者によって処理されます。  
  
 [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC API 関数では、これらのキーワードと値の一部をパラメーターとして使用できます。
