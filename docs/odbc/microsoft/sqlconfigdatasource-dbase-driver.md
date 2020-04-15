---
title: データ ソースを変換する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], dBASE Driver
ms.assetid: 19909902-054c-4e19-9c06-a212aace13fe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 18c6721b4f34772e8c3cd8e4f515233f80566fb3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283972"
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 データ**ソース**の追加、変更、または削除に使用される関数は、次のキーワードを動的に使用します。  
  
|Keyword|説明|  
|-------------|-----------------|  
|照合シーケンス|フィールドを並べ替える順序。<br /><br /> シーケンスは、ASCII (デフォルト) または国際形式のいずれかです。<br /><br /> これにより、設定ダイアログボックスの**照合順序**と同じオプションが設定されます。|  
|デフォルトの DIR|ディレクトリへのパス指定。|  
|DELETED|dBASE ドライバーの場合、削除済みとしてマークされた行を取得または配置できるかどうかを指定します。 1 に設定すると、削除された行は表示されません。0 に設定すると、削除された行は削除されていない行と同じように扱われます。<br /><br /> これにより、設定ダイアログボックスで削除**された行を表示**するオプションと同じオプションが設定されます。|  
|Description|データ ソース内のデータの説明。<br /><br /> これにより、セットアップ ダイアログ ボックスで**説明**と同じオプションが設定されます。|  
|DRIVER|ドライバ DLL へのパス指定。|  
|ドライバー ID|ドライバーの整数 ID。<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5.0)|  
|フィル|ファイルタイプ dBase III、dBase IV、または dBase 5|  
|ページタイムアウト|ページが削除される前にバッファー内に残る時間を 10 分の 1 秒で指定します。 デフォルトは 600 分の 1 秒 (60 秒) です。 このオプションは、ODBC ドライバを使用するすべてのデータ ソースに適用されます。<br /><br /> 設定ダイアログボックスでページ**タイムアウト**と同じオプションを設定します。|  
|READONLY|ファイルを読み取り専用にする場合は TRUE。ファイルを読み取り専用にしない場合は FALSE。<br /><br /> 設定ダイアログボックスで同じオプションを**読み取り専用**に設定します。|  
|STATISTICS|dBASE ドライバーの場合、テーブル サイズの統計情報が近似されるかどうかを判断します。 このオプションは、ODBC ドライバを使用するすべてのデータ ソースに適用されます。<br /><br /> 設定ダイアログボックスで、同じオプションを **「おおよその行数**」と設定します。|  
|スレッド|使用するエンジンのバックグラウンド スレッドの数。 この値は 3 で、変更できません。<br /><br /> これにより、設定ダイアログボックスの**スレッドと**同じオプションが設定されます。|
