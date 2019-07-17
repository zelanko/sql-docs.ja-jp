---
title: ODBCCONF します。EXE |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d7934226ec489af0ac0b1f655c7d27660cb6a928
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996271"
---
# <a name="odbcconfexe"></a>ODBCCONF します。実行可能ファイル
ODBCCONF.exe は、ODBC ドライバーとデータ ソース名を構成することができるコマンド ライン ツールです。  
  
> [!NOTE]  
>  ODBCCONF.exe は、Windows Data Access Components の将来のバージョンで削除されます。 この機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーとデータ ソースを管理するのに PowerShell コマンドを使用することができます。 これらの PowerShell コマンドの詳細については、次を参照してください。 [Windows Data Access Components コマンドレット](https://technet.microsoft.com/library/hh771019.aspx)します。  
  
## <a name="syntax"></a>構文  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>引数  
 *スイッチ*  
 0 個以上のスイッチ オプション。 使用可能なスイッチの一覧で、このトピックの後半の「解説」を参照してください。  
  
 *action*  
 1 つのアクションを実行します。 使用可能なオプションの一覧で、「解説」を参照してください。  
  
## <a name="remarks"></a>コメント  
 次のスイッチを使用できます。  
  
|スイッチ|説明|  
|------------|-----------------|  
|/A {*アクション*}|アクションを指定します。<br /><br /> 1 つのアクションが指定した場合のみ、/A は省略可能です。|  
|/?|ODBCCONF の使用状況を表示します。実行可能ファイルです。|  
|/C|処理するには、アクションが失敗したかどうかは続行されます。|  
|/E|/F 処理が完了したときに指定した応答ファイルを消去します。|  
|/F|応答ファイルを使用して`odbcconf /F my.rsp`します。<br /><br /> my.rsp は、次のようになります。 `REGSVR c:\my.dll`<br /><br /> /A は、応答ファイルでは使用されません。|  
|/H|使用率 (ヘルプ) を表示します。 このスイッチは、同じ/ですか。|  
|/L[*mode*] *filename*|次の 3 つのモードのいずれかのファイルをプログラムの出力を送信します。 標準 (n)、詳細な (v)、およびデバッグ (d)。 モードのレコード odbcconf.exe によって読み込まれる Dll をデバッグします。<br /><br /> /L を指定するには、モードを使用せず、ログ ファイルが空になります。<br /><br /> たとえば、 **/Lv log.txt**します。|  
|/R|アクションは、再起動後に実行されます。|  
|/S|サイレント モード。 エラー メッセージは表示されません。|  
  
 次の操作を使用できます。  
  
|操作|説明|  
|------------|-----------------|  
|CONFIGDRIVER *driver_name * * params のドライバー固有の構成*|適切なドライバーのセットアップ DLL と呼び出しを読み込み、 **ConfigDriver**関数。<br /><br /> 等価の[SQLConfigDriver 関数](../odbc/reference/syntax/sqlconfigdriver-function.md)します。<br /><br /> 以下に例を示します。<br /><br /> /A {CONFIGDRIVER「ドライバ名」"CPTimeout = 60"}<br /><br /> /A {CONFIGDRIVER「ドライバ名」"DriverODBCVer 03.80 ="}|  
|CONFIGDSN *driver_name* DSN =*名前* &#124; *属性*|追加またはシステム データ ソースを変更します。<br /><br /> 等価の[SQLConfigDataSource 関数](../odbc/reference/syntax/sqlconfigdatasource-function.md)します。<br /><br /> 以下に例を示します。<br /><br /> /A {CONFIGDSN "SQL Server" "DSN=name &#124; Server=srv"}|  
|CONFIGSYSDSN *driver_name* DSN =*名前* &#124; *属性*|追加またはシステム データ ソースを変更します。<br /><br /> 等価の[SQLConfigDataSource 関数](../odbc/reference/syntax/sqlconfigdatasource-function.md)します。<br /><br /> 以下に例を示します。<br /><br /> /A {CONFIGSYSDSN "SQL Server" "DSN=name &#124; Server=srv"}|  
|INSTALLDRIVER|等価[SQLInstallDriverEx 関数](../odbc/reference/syntax/sqlinstalldriverex-function.md)します。<br /><br /> INSTALLDRIVER に渡されるキーワードと値のペアの構文については、次を参照してください。[ドライバーの仕様のサブキー](../odbc/reference/install/driver-specification-subkeys.md)します。<br /><br /> 以下に例を示します。<br /><br /> /A {INSTALLDRIVER"には、ドライバー &#124; Driver=c:\your.dll &#124; Setup=c:\your.dll &#124; APILevel = 2 &#124; ConnectFunctions = YYY &#124; DriverODBCVer = 03.50 &#124; FileUsage = 0 &#124; SQLLevel = 1"}|  
|INSTALLTRANSLATOR *translator 構成 * * ドライバーのパス*|翻訳者にに関する情報を追加、**見つかりました。INI\ODBC トランスレーター**レジストリ キー。<br /><br /> 等価[SQLInstallTranslatorEx 関数](../odbc/reference/syntax/sqlinstalltranslatorex-function.md)します。<br /><br /> INSTALLDRIVER に渡されるキーワードと値のペアの構文については、次を参照してください。[仕様のサブキー](../odbc/reference/install/translator-specification-subkeys.md)します。<br /><br /> 以下に例を示します。<br /><br /> /A {INSTALLTRANSLATOR  "My Translator &#124; Translator=c:\my.dll &#124; Setup=c:\my.dll"}|  
|REGSVR *dll*|DLL を登録します。<br /><br /> Regsvr32.exe と等価です。<br /><br /> 以下に例を示します。<br /><br /> /A {REGSVR c:\my.dll}|  
|SETFILEDSNDIR|ときに HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC します。INI\ODBC ファイル DSN\DefaultDSNDir が存在しない、SETFILEDSNDIR アクションはそれが作成され、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir、\ODBC\Data ソースで追加の値を割り当てます。<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC 値です。INI\ODBC ファイル DSN\DefaultDSNDir では、ファイル ベースのデータ ソースを作成するときにでは、ODBC データ ソース アドミニストレーターを使用する既定の場所を指定します。<br /><br /> 以下に例を示します。<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>参照  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
