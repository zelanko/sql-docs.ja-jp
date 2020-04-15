---
title: SQLConfig データソース (テキスト ファイル ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d2809f9b15dd6843e4404c7cf1887c3caa015a3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283922"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 データ**ソース**の追加、変更、または削除に使用される関数は、次のキーワードを動的に使用します。  
  
|Keyword|説明|  
|-------------|-----------------|  
|文字セット|テキスト ドライバの場合は、OEM または ANSI。|  
|コルネームヘッダー|テキスト ドライバーの場合、データの最初のレコードが列名を指定するかどうかを示します。 TRUE または FALSE です。|  
|デフォルトの DIR|ディレクトリへのパス指定。|  
|Description|データ ソース内のデータの説明。<br /><br /> これにより、セットアップ ダイアログ ボックスで**説明**と同じオプションが設定されます。|  
|DRIVER|ドライバ DLL へのパス指定。|  
|ドライバー ID|ドライバーの整数 ID。 27 (テキスト)|  
|拡張 機能|データ ソース上のテキスト ファイルのファイル名拡張子を一覧表示します。<br /><br /> これにより、[設定] ダイアログ ボックスの **[拡張子リスト] と**同じオプションが設定されます。|  
|フィル|ファイルタイプ テキスト|  
|Filetype|テキスト ドライバー (テキスト) のファイルの種類。|  
|FORMAT|テキスト・ドライバーの場合は、固定長、タブ区切り文字、CSV区切り文字 (コンマで指定) 、または DELIMITED() (括弧内に指定された特殊文字によって) を指定できます。 特殊文字は 1 文字の長さで、文字、10 進数、または 16 進数の形式で指定できます。|  
|マックスカンロウズ|既存のデータに基づいて列のデータ型を設定するときにスキャンされる行の数。<br /><br /> テキスト ドライバーの場合、スキャンする行数として 1 ~ 32767 の数値を入力できます。ただし、この値は常に 25 に設定されます。 (制限を超えた数値はエラーを返します。<br /><br /> 設定ダイアログボックスで **、同じオプションを[スキャンする行**]と同じオプションを設定します。|  
|READONLY|ファイルを読み取り専用にする場合は TRUE。ファイルを読み取り専用にしない場合は FALSE。<br /><br /> 設定ダイアログボックスで同じオプションを**読み取り専用**に設定します。|
