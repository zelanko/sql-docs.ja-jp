---
title: "SQLConfigDataSource (テキスト ファイル ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b26eba11563baeef77e0fc47597a50776c5dc179
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLConfigDataSource**を追加するに使用される関数は、次の変更、または削除、データ ソースが動的に次のキーワードを使用します。  
  
|Keyword|Description|  
|-------------|-----------------|  
|文字セット|OEM または ANSI テキスト ドライバー。|  
|は|テキスト、ドライバーのデータの最初のレコードが、列名を指定するかどうかを示します。 TRUE または FALSE のいずれか。|  
|DEFAULTDIR|ディレクトリ パスの指定。|  
|DESCRIPTION|データ ソース内のデータの説明です。<br /><br /> 同じオプションを設定**説明**設定 ダイアログ ボックスをオンにします。|  
|DRIVER|ドライバー DLL にパス指定します。|  
|DRIVERID|ドライバーの整数 ID です。 27 (テキスト)|  
|拡張機能|データ ソース上のテキスト ファイルのファイル名拡張子の一覧を表示します。<br /><br /> として同じオプションを設定**拡張機能リスト**設定 ダイアログ ボックスをオンにします。|  
|FIL|ファイルの種類のテキスト|  
|ファイルの種類|テキスト ドライバー (テキスト) のファイルの種類。|  
|FORMAT|テキスト ドライバーの FIXEDLENGTH、TABDELIMITED、CSVDELIMITED (コンマ)、またはできます DELIMITED() (によって、かっこで指定された特殊文字)。 特殊文字 1 つの文字の長さでは、文字、10 進数または 16 進数形式であることができます。|  
|MAXSCANROWS|既存のデータに基づいて、列のデータ型を設定する場合にスキャンする行の数。<br /><br /> テキスト ドライバーのできます番号を入力する、1 から 32767 まで; をスキャンする行の数ただし、この値は常に既定値 25。 (制限外の数値はエラーを返します。)<br /><br /> として同じオプションを設定**スキャンする行数**設定 ダイアログ ボックスをオンにします。|  
|READONLY|読み取り専用ファイルを作成する場合は TRUE読み取り専用ファイルを作成する場合は FALSE。<br /><br /> 同じオプションを設定**読み取り専用**設定 ダイアログ ボックスをオンにします。|
