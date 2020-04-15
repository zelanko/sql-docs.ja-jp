---
title: ODBCCONF.EXE |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d771f01d292312f8a0f0060c16e3c348bf2e009e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307533"
---
# <a name="odbcconfexe"></a>ODBCCONF.Exe
ODBCCONF.exe は、ODBC ドライバとデータ ソース名を設定できるコマンド ライン ツールです。  
  
> [!NOTE]  
>  ODBCCONF.exe は、将来のバージョンの Windows データ アクセス コンポーネントで削除される予定です。 この機能の使用を避け、現在この機能を使用しているアプリケーションを変更するように計画してください。 PowerShell コマンドを使用して、ドライバーとデータ ソースを管理できます。 これらの PowerShell コマンドの詳細については[、「Windows データ アクセス コンポーネントのコマンドレット](/powershell/module/wdac)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>引数  
 *スイッチ*  
 0 個以上のスイッチ オプション。 使用可能なスイッチの一覧については、このトピックの後半の「解説」を参照してください。  
  
 *action*  
 実行する 1 つの操作。 使用可能なオプションの一覧については、「解説」を参照してください。  
  
## <a name="remarks"></a>解説  
 次のスイッチが使用できます。  
  
|Switch|説明|  
|------------|-----------------|  
|/A {*アクション*}|アクションを指定します。<br /><br /> /A は、1 つのアクションのみが指定されている場合は省略可能です。|  
|/?|ODBCCONF の表示の使用法。Exe。|  
|/C|アクションが失敗した場合、処理は続行されます。|  
|/E|処理が終了したら/F で指定された応答ファイルを消去します。|  
|/F|応答`odbcconf /F my.rsp`ファイルを使用します。<br /><br /> my.rsp は次のようになります。`REGSVR c:\my.dll`<br /><br /> /A は応答ファイルでは使用されません。|  
|/H|表示の使用状況 (ヘルプ)。 このスイッチは /?と同じです。|  
|/L[*モード*]*ファイル名*|プログラム出力を、通常 (n)、詳細 (v)、デバッグ (d) の 3 つのモードのいずれかでファイルに送信します。 デバッグ モードでは、odbcconf.exe によって読み込まれる DLL が記録されます。<br /><br /> モードを指定せずに /L を指定すると、ログ ファイルは空になります。<br /><br /> たとえば **、/Lv log.txt を参照してください**。|  
|/R|このアクションは再起動後に実行されます。|  
|/S|サイレント モード。 エラー メッセージを表示しません。|  
  
 次のオプションがあります｡  
  
|アクション|説明|  
|------------|-----------------|  
|ドライバー *driver_name**ドライバー固有の構成パラメーター*|適切なドライバー セットアップ DLL を読み込み、**関数を**呼び出します。<br /><br /> [関数と](../odbc/reference/syntax/sqlconfigdriver-function.md)同等です。<br /><br /> 次に例を示します。<br /><br /> /A {構成ドライバー " ドライバー名" "CPTimeout=60"}<br /><br /> /A {構成ドライバー " ドライバー名" "ドライバー ODBCVer=03.80"}|  
|DSN=*名前*&#124;*属性**をdriver_name*する|システム データ ソースを追加または変更します。<br /><br /> [関数と](../odbc/reference/syntax/sqlconfigdatasource-function.md)同等です。<br /><br /> 次に例を示します。<br /><br /> /A {CONFIGDSN "SQL サーバー" "DSN=名前&#124;サーバー=srv"}|  
|DSN=*名前*&#124;*属性**driver_name* DSN=|システム データ ソースを追加または変更します。<br /><br /> [関数と](../odbc/reference/syntax/sqlconfigdatasource-function.md)同等です。<br /><br /> 次に例を示します。<br /><br /> /A {SQL サーバー" "DSN=名前&#124;サーバー =srv" }|  
|ドライバーをインストールします。|[関数](../odbc/reference/syntax/sqlinstalldriverex-function.md)と同等です。<br /><br /> INSTALLDRIVER に渡されるキーワードと値のペアの構文については、[ドライバー仕様サブキー](../odbc/reference/install/driver-specification-subkeys.md)を参照してください。<br /><br /> 次に例を示します。<br /><br /> /A {インストールドライバー "ドライバー&#124;ドライバー=c:\あなたの.dll&#124;セットアップ=c:\あなたの.dll &#124; apilevel=2 &#124;コネクトファンクション=YYy&#124;ドライバODBCVer=03.50&#124;ファイルの使用=0&#124; SQLLevel=1"}|  
|トランス*レータ構成**ドライバパスの*インストール|トランスレータに関する情報を**HKEY_LOCAL_MACHINE\ソフトウェア\ODBC\ODBCINST に追加します。INI\ODBC トランスレータの**レジストリ キー。<br /><br /> [関数に](../odbc/reference/syntax/sqlinstalltranslatorex-function.md)相当する 。<br /><br /> INSTALLDRIVER に渡されるキーワード値ペア構文については、[変換プログラム仕様サブキー](../odbc/reference/install/translator-specification-subkeys.md)を参照してください。<br /><br /> 次に例を示します。<br /><br /> /A {トランスレータ "翻訳者&#124;翻訳者=c:\my.dll &#124;セットアップ=c:\my.dll"}|  
|DLL *dll*|DLL を登録します。<br /><br /> regsvr32.exe と同等です。<br /><br /> 次に例を示します。<br /><br /> /A {REGSVR c:\my.dll}|  
|ファイル DSNDIR を設定します。|HKEY_LOCAL_MACHINE\ソフトウェア\ODBC\ODBC を使用する場合。INI\ODBC ファイル DSN\既定 DSNDir が存在しない場合、SETFILEDSNDIR アクションが作成し、\ODBC\データ ソースが追加されたHKEY_LOCAL_MACHINE\SOFTWARE\Windows\現在のバージョン\コモンファイルディレクトリの値を割り当てます。<br /><br /> HKEY_LOCAL_MACHINE\ソフトウェア\ODBC\ODBC の値。INI\ODBC ファイル DSN\既定 DSNDir は、ファイル ベースのデータ ソースを作成するときに ODBC データ ソース アドミニストレータが使用する既定の場所を指定します。<br /><br /> 次に例を示します。<br /><br /> /A {ファイル DSNDIR}|  
  
## <a name="see-also"></a>参照  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
