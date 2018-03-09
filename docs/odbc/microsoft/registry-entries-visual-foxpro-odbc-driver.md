---
title: "レジストリ エントリ (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9d776df7e758f0902ca3b20a94f8c40e351e959
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>レジストリ エントリ (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーをインストールするときに、インストール プログラムは Microsoft Visual FoxPro ドライバーと呼ばれる新しいキーを追加する、HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini のレジストリ キーに、システムのレジストリを更新します。 そのキーの下では、次の表で説明する値が追加されます。  
  
|値の名前|[値の型]|[値]|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|"YYN"|  
|Driver|REG_SZ|システム ファイルのパスを vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"*.dbf,\*.cdx,\*.fpt"|  
|FileUsage|REG_SZ|"1"|  
|セットアップ|REG_SZ|システム ファイルのパスを vfpodbc.dll|  
|SQLLevel|REG_SZ|"0"|  
  
 インストール プログラムでは、"Visual FoxPro Files", システムの HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini キーへの既定の Visual FoxPro ドライバーを表すキーも追加します。 このキーの下では、インストール プログラムは、次の表で説明する値を追加します。  
  
|値の名前|[値の型]|[値]|  
|----------------|----------------|-----------|  
|Driver|REG_SZ|システム ファイルのパスを vfpodbc.dll|  
  
 Visual FoxPro ODBC データ ソース、ODBC の構成に追加するたびに新しいキーがそのデータ ソース名が追加されます。 データ ソースの値に設定する値に対応して、 **ODBC Visual FoxPro セットアップ**ダイアログ ボックスで、次の表に記載されています。  
  
|値の名前 (キーワード)|[値の型]|[値]|  
|----------------------------|----------------|-----------|  
|[部単位で印刷]|REG_SQ|サポートされる照合順序|  
|Description|REG_SZ|データ ソースのユーザーの説明|  
|Driver||システム ファイルのパスを vfpodbc.dll|  
|[Exclusive]||はい、いいえ|  
|BackgroundFetch||はい、いいえ|  
|SourceDB|REG_SZ|パス。DBC ファイル|  
|[SourceType]|REG_SZ|"DBC"または"DBF"|  
  
 この情報を直接アクセスしないでください。レジストリのすべての管理には、追加、変更、またはデータ ソースを削除するときに ODBC アドミニストレーターによっては処理されます。  
  
 これらのキーワードと値の一部を使用するにはパラメーターとして、 [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC API 関数。
