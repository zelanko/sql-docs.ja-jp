---
title: "ODBC Jet SQLConfigDataSource (Excel ドライバー) |Microsoft ドキュメント"
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
- SQLConfigDataSource function [ODBC], Excel Driver
- Excel driver [ODBC], SqlConfigDataSource
ms.assetid: 885b3bea-f4b6-4902-b994-f78a912b612f
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 16ae2bb0432feaa80b005a5817bd44258829acbe
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet SQLConfigDataSource (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバーに固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLConfigDataSource**を追加するに使用される関数は、次の変更、または削除、データ ソースが動的に次のキーワードを使用します。  
  
|Keyword|Description|  
|-------------|-----------------|  
|DBQ|Excel ドライバーの Microsoft Excel 5.0 またはそれ以降のファイルにアクセスするときにブック ファイルの名前。<br /><br /> これと同じオプションを設定**データベース**設定 ダイアログ ボックスをオンにします。|  
|DEFAULTDIR|ディレクトリ パスの指定。<br /><br /> として同じオプションを設定**ディレクトリの選択**または**ブックの選択**設定 ダイアログ ボックスをオンにします。|  
|DESCRIPTION|データ ソース内のデータの説明です。<br /><br /> 同じオプションを設定**説明**設定 ダイアログ ボックスをオンにします。|  
|DRIVER|ドライバー DLL にパス指定します。|  
|DRIVERID|ドライバーの整数 ID です。<br /><br /> 534 (Microsoft Excel 3.0)<br /><br /> 278 (Microsoft Excel 4.0)<br /><br /> 22 (Microsoft Excel 5.0 または 7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|FIL|ファイルの種類、たとえば、Excel 3.0、Excel 4.0、Excel 5.0、Excel 7.0、Excel 97、Excel 2000、または Excel 2003。|  
|消えて|か、範囲の最初の行のセルが、テーブルの列名、(1) を含めるかどうかを示します (0) です。|  
|MAXSCANROWS|既存のデータに基づいて、列のデータ型を設定する場合にスキャンする行の数。<br /><br /> 16 ~ 1 の数値は、スキャンする行数を入力できます。 値の既定値は 8 です。0 に設定されている場合は、すべての行がスキャンされます。 (制限外の数値はエラーを返します。)<br /><br /> として同じオプションを設定**スキャンする行数**設定 ダイアログ ボックスをオンにします。|  
|READONLY|読み取り専用ファイルを作成する場合は TRUE読み取り専用ファイルを作成する場合は FALSE。<br /><br /> 同じオプションを設定**読み取り専用**設定 ダイアログ ボックスをオンにします。|  
|スレッド|使用する、エンジンのバック グラウンド スレッドの数。 Microsoft Access ドライバーは、この値は、既定値は 3 が、変更することができます。 DBASE、MicrosoftExceldriver この値は、3 は変更できません。<br /><br /> 同じオプションを設定**スレッド**設定 ダイアログ ボックスをオンにします。|
