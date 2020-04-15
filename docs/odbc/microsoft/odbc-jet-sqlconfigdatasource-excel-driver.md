---
title: ODBC ジェット SQL 構成データ ソース (Excel ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Excel Driver
- Excel driver [ODBC], SqlConfigDataSource
ms.assetid: 885b3bea-f4b6-4902-b994-f78a912b612f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a76482acd1182d900336d7ac9826b16968e00caa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293012"
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet SQLConfigDataSource (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 データ**ソース**の追加、変更、または削除に使用される関数は、次のキーワードを動的に使用します。  
  
|Keyword|説明|  
|-------------|-----------------|  
|DBQ|Excel 5.0 以降のファイルにアクセスする場合の Excel ドライバの場合は、ブック ファイルの名前を指定します。<br /><br /> これにより、セットアップ ダイアログ ボックスで**データベース**と同じオプションが設定されます。|  
|デフォルトの DIR|ディレクトリへのパス指定。<br /><br /> 設定ダイアログボックスで、同じオプションを **「ディレクトリの選択」** または **「ワークブックの選択**」と同じオプションを設定します。|  
|Description|データ ソース内のデータの説明。<br /><br /> これにより、セットアップ ダイアログ ボックスで**説明**と同じオプションが設定されます。|  
|DRIVER|ドライバ DLL へのパス指定。|  
|ドライバー ID|ドライバーの整数 ID。<br /><br /> 534 (Excel 3.0)<br /><br /> 278 (Excel 4.0)<br /><br /> 22 (Excel 5.0/7.0)<br /><br /> 790 (Excel 97-2003)|  
|フィル|Excel 3.0、Excel 4.0、Excel 5.0、Excel 7.0、Excel 97、Excel 2000、Excel 2003 などのファイルの種類。|  
|ファーストロウハスネーム|範囲の最初の行のセルに、テーブルの列名 (1) が含まれているかどうかを示します (0)。|  
|マックスカンロウズ|既存のデータに基づいて列のデータ型を設定するときにスキャンされる行の数。<br /><br /> スキャンする行には、1 から 16 までの数値を入力できます。 デフォルト値は 8 です。0 に設定すると、すべての行がスキャンされます。 (制限を超えた数値はエラーを返します。<br /><br /> 設定ダイアログボックスで **、同じオプションを[スキャンする行**]と同じオプションを設定します。|  
|READONLY|ファイルを読み取り専用にする場合は TRUE。ファイルを読み取り専用にしない場合は FALSE。<br /><br /> 設定ダイアログボックスで同じオプションを**読み取り専用**に設定します。|  
|スレッド|使用するエンジンのバックグラウンド スレッドの数。 Access ドライバの場合、この値はデフォルトで 3 ですが、変更できます。 dBASE の場合、この値は 3 であり、変更できません。<br /><br /> これにより、設定ダイアログボックスの**スレッドと**同じオプションが設定されます。|
