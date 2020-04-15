---
title: レジストリ エントリ (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304839"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>レジストリ エントリ (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーをインストールすると、インストール プログラムはレジストリ キー HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini のレジストリ キーでシステムのレジストリを更新し、Microsoft Visual FoxPro ドライバーと呼ばれる新しいキーを追加します。 このキーの下に、次の表に示す値が追加されます。  
  
|値の名前|値の型|[値]|  
|----------------|----------------|-----------|  
|アピレレベル|REG_SZ|"1"|  
|関数を接続する|REG_SZ|「YYN」|  
|Driver|REG_SZ|vfpodbc.dll ファイルへのシステム パス|  
|DriverODBCVer|REG_SZ|"02.50"|  
|ファイルの拡張|REG_SZ|"*.dbf,\*.cdx,\*.fpt"|  
|ファイルの使用法|REG_SZ|"1"|  
|セットアップ|REG_SZ|vfpodbc.dll ファイルへのシステム パス|  
|SQL レベル|REG_SZ|"0"|  
  
 インストール プログラムでは、既定の Visual FoxPro ドライバーを表すキー "Visual FoxPro ファイル" もシステムの HKEY_CURRENT_USER\SOFTWARE\ODBC\ODBC.ini キーに追加されます。 このキーの下に、インストール プログラムは次の表に示す値を追加します。  
  
|値の名前|値の型|[値]|  
|----------------|----------------|-----------|  
|Driver|REG_SZ|vfpodbc.dll ファイルへのシステム パス|  
  
 VISUAL FoxPro ODBC データ ソースを ODBC 構成に追加するたびに、そのデータ ソース名に新しいキーが追加されます。 データ ソースの値は、次の表に示すように **、ODBC Visual FoxPro の [セットアップ**] ダイアログ ボックスで設定した値に対応します。  
  
|値名 (キーワード)|値の型|[値]|  
|----------------------------|----------------|-----------|  
|[部単位で印刷]|REG_SQ|サポートされている照合順序|  
|説明|REG_SZ|データ ソースのユーザー説明|  
|Driver||vfpodbc.dll ファイルへのシステム パス|  
|排他的||はい、いいえ|  
|バックグラウンドフェッチ||はい、いいえ|  
|SourceDB|REG_SZ|へのパス 。DBC ファイル|  
|SourceType|REG_SZ|"DBC" または "DBF"|  
  
 この情報に直接アクセスしないでください。データ ソースを追加、変更、または削除すると、レジストリの管理は ODBC アドミニストレータによって処理されます。  
  
 これらのキーワードと値の一部を[、SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC API 関数のパラメーターとして使用できます。
