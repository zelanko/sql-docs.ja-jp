---
title: SQLConfigDataSource (dBASE ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], dBASE Driver
ms.assetid: 19909902-054c-4e19-9c06-a212aace13fe
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa98f819b1774860aacc330bc393b000ab34155e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLConfigDataSource**を追加するに使用される関数は、次の変更、または削除、データ ソースが動的に次のキーワードを使用します。  
  
|Keyword|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|フィールドが並べ替えられたシーケンスです。<br /><br /> シーケンスを指定できます: 並べ (既定)。<br /><br /> として同じオプションを設定**照合シーケンス**設定 ダイアログ ボックスをオンにします。|  
|DEFAULTDIR|ディレクトリ パスの指定。|  
|DELETED|DBASE ドライバーの削除済みとしてマークされている行の取得やに配置されているかどうかを指定します。 場合 1 の場合、削除された行に設定するには表示されません。0 の場合、削除された行に設定されている場合、削除されていない行と同様に扱わです。<br /><br /> として同じオプションを設定**削除行の表示**設定 ダイアログ ボックスをオンにします。|  
|DESCRIPTION|データ ソース内のデータの説明です。<br /><br /> 同じオプションを設定**説明**設定 ダイアログ ボックスをオンにします。|  
|DRIVER|ドライバー DLL にパス指定します。|  
|DRIVERID|ドライバーの整数 ID です。<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5.0)|  
|FIL|ファイル dBase III、IV、dBase ファイルまたは dBase 5 を入力|  
|PAGETIMEOUT|部分ページ (使用しない場合) が削除される前にバッファーに残っている 1 秒の 1/10 で時間の期間を指定します。 既定値は 600 秒 (60 秒) の部分の 1/10。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されることに注意してください。<br /><br /> 同じオプションを設定**ページのタイムアウト**設定 ダイアログ ボックスをオンにします。|  
|READONLY|読み取り専用ファイルを作成する場合は TRUE読み取り専用ファイルを作成する場合は FALSE。<br /><br /> 同じオプションを設定**読み取り専用**設定 ダイアログ ボックスをオンにします。|  
|STATISTICS|DBASE ドライバーのテーブルのサイズの統計情報を概算するかどうかを判断します。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されることに注意してください。<br /><br /> として同じオプションを設定**行のカウントの概数**設定 ダイアログ ボックスをオンにします。|  
|スレッド|使用する、エンジンのバック グラウンド スレッドの数。 この値は 3 であるため、変更できません。<br /><br /> 同じオプションを設定**スレッド**設定 ダイアログ ボックスをオンにします。|
