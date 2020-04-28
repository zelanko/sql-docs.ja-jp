---
title: サポートされていない Visual FoxPro のコマンドと関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- FoxPro ODBC driver [ODBC], commands and functions
- functions [ODBC], Visual FoxPro
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro commands and functions
- FoxPro ODBC driver
ms.assetid: afdb6b7e-738d-42ca-8053-67ae50873ca6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e5b8ed06ad9f996d644df0dfb99d15adcff86bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307653"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>サポートされていない Visual FoxPro コマンドと関数 (Visual FoxPro ODBC ドライバー)
次の表に、Visual foxpro ODBC ドライバーではサポートされていないが、Microsoft® Visual FoxPro®でサポートされている FoxPro コマンドと関数の一覧を示します。  
  
 アプリケーションが、ルール、トリガー、既定値、またはストアドプロシージャがこれらの Visual FoxPro コマンドまたは関数を呼び出すデータと対話する場合、ドライバーはエラーを生成することがあります。  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>サポートされていない Visual FoxPro のコマンドと関数  
  
||||  
|-|-|-|  
|#DEFINE... #UNDEF|#IF... #ENDIF プリプロセッサディレクティブ|#IFDEF &#124; #IFNDEF|  
|#INCLUDE プリプロセッサディレクティブ|:: スコープ解決演算子|! コマンド (RUN &#124; を参照してください。 メニュー|  
|? &#124; しますか? コマンド|??? コマンド|\ &#124; \\\ コマンド|  
|@ ...BOX コマンド|@ ...クラスコマンド|@ ...CLEAR コマンド|  
|@ ...エディットボックスの編集コマンド|@ ...FILL コマンド|@ ...取得|  
|@ ...メニューコマンド|@ ...プロンプトコマンド|@ ...コマンドを言います。|  
|@ ...SCROLL コマンド|@ ...TO コマンド||  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ACCEPT コマンド|ACLASS () 関数|[アクティブ化] メニューコマンド|  
|ポップアップコマンドのアクティブ化|画面のアクティブ化コマンド|ウィンドウのアクティブ化コマンド|  
|ActivateCell メソッド|クラスの追加コマンド|"R () 関数"|  
|AFONT () 関数|AINSTANCE () 関数|_ALIGNMENT システムメモリ変数|  
|AMEMBERS () 関数|ANSITOOEM () 関数|APRINTERS () 関数|  
|ASELOBJ () 関数|支援コマンド||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BAR () 関数|BARCOUNT () 関数|BARPROMPT () 関数|  
|_BEAUTIFY システムメモリ変数|_BOX システムメモリ変数|参照コマンド|  
|_BROWSER システムメモリ変数|アプリのビルドコマンド|ビルド EXE コマンド|  
|プロジェクトのビルドコマンド|_BUILDER システムメモリ変数||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|_CALCVALUE システムメモリ変数|_CLIPTEXT システムメモリ変数|_CONVERTER システムメモリ変数|  
|_CUROBJ システムメモリ変数|CALL コマンド|CANCEL コマンド|  
|CAPSLOCK () 関数|CD コマンド|コマンドの変更|  
|CHDIR コマンド|CHRSAW () 関数|メモコマンドを閉じる|  
|CNTBAR () 関数|CNTPAD () 関数|COL () 関数|  
|COMPILE コマンド|データベースのコンパイルコマンド|フォームのコンパイルコマンド|  
|COMPOBJ () 関数|Container オブジェクト|Control オブジェクト|  
|ファイルのコピーコマンド|メモのコピーコマンド|クラスの作成コマンド|  
|CREATE CLASSLIB コマンド|カラーセットの作成コマンド|CREATE コマンド|  
|接続の作成コマンド|CREATE DATABASE コマンド|フォームの作成コマンド|  
|コマンドから作成|ラベルの作成コマンド|メニューコマンドの作成|  
|プロジェクトの作成コマンド|CREATE QUERY コマンド|レポートの作成コマンド|  
|画面の作成コマンド|SQL ビューの作成コマンド|CREATE TRIGGER コマンド|  
|ビューの作成コマンド|CREATEOBJECT () 関数|CURDIR () 関数|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|_DBLCLICK システムメモリ変数|_DIARYDATE システムメモリ変数|DBSETPROP () 関数|  
|DDE 関数|[非アクティブ化] メニューコマンド|ポップアップコマンドの非アクティブ化|  
|ウィンドウの非アクティブ化コマンド|DECLARE DLL コマンド|DECLARE コマンド|  
|BAR コマンドの定義|[定義] ボックスコマンド|クラスの定義コマンド|  
|[定義] メニューコマンド|PAD の定義コマンド|ポップアップコマンドの定義|  
|ウィンドウコマンドの定義|接続コマンドの削除|データベースの削除コマンド|  
|ファイルの削除コマンド|DELETE トリガーコマンド|ビューの削除コマンド|  
|DIR コマンド|DIRECTORY コマンド|表示コマンド|  
|接続の表示コマンド|データベースコマンドの表示|DLL の表示コマンド|  
|ファイルの表示コマンド|DISPLAY MEMORY コマンド|オブジェクトの表示コマンド|  
|DISPLAY PROCEDURES コマンド|ステータスの表示コマンド|構造の表示コマンド|  
|テーブルの表示コマンド|表示ビューコマンド|DO FORM コマンド|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|[編集] コマンド|エラーコマンド||  
|ERASE コマンド|外部コマンド|EXPORT コマンド|  
|EJECT コマンド|ページの取り出しコマンド||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|_FOXDOC システムメモリ変数|_FOXGRAPH システムメモリ変数|FEOF () 関数|  
|FCLOSE () 関数|FCREATE () 関数|FGETS () 関数|  
|FERROR () 関数|FFLUSH () 関数|FKLABEL () 関数|  
|フィルターコマンド|FIND コマンド|FOPEN () 関数|  
|FKMAX () 関数|FONTMETRIC () 関数|FSEEK () 関数|  
|FPUTS () 関数|FREAD () 関数||  
|FWRITE () 関数|FCHSIZE () 関数||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|_GENGRAPH システムメモリ変数|_GENMENU システムメモリ変数|_GENPD システムメモリ変数|  
|_GENSCRN システムメモリ変数|_GENXTAB システムメモリ変数|GETBAR () 関数|  
|GETCOLOR () 関数|GETDIR () 関数|GETEXPR コマンド|  
|GETFILE () 関数|GETFONT () 関数|GETOBJECT () 関数|  
|GETPAD () 関数|GETPICT () 関数|GETPRINTER () 関数|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|ヘルプコマンド|メニューコマンドを非表示にする|ポップアップコマンドを非表示にする|  
|ウィンドウの非表示コマンド|HOME () 関数||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IMESTATUS () 関数|IMPORT コマンド|入力コマンド|  
|コマンドのインデックス|INKEY () 関数|ISCOLOR () 関数|  
|INSERT コマンド|プラグインモード () 関数||  
|ISMOUSE () 関数|_INDENT システムメモリ変数||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|JOIN コマンド|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|キーボードコマンド|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|_LMARGIN システムメモリ変数|LABEL コマンド|LASTKEY () 関数|  
|LINENO) 関数|コマンドの一覧表示|接続の一覧表示コマンド|  
|LOAD コマンド|LOCFILE () 関数||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCOL () 関数|MD コマンド|メニューをコマンドに|  
|MEMORY () 関数|メニューコマンド|MKDIR コマンド|  
|MENU () 関数|MESSAGEBOX () 関数|接続の変更コマンド|  
|クラスの変更コマンド|MODIFY コマンドコマンド|フォームの変更コマンド|  
|データベースの変更コマンド|MODIFY FILE コマンド|メモコマンドの変更|  
|全般コマンドの変更|ラベルの変更コマンド|プロジェクトの変更コマンド|  
|メニューコマンドの変更|プロシージャコマンドの変更|画面の変更コマンド|  
|クエリコマンドの変更|レポートの変更コマンド|ウィンドウの変更コマンド|  
|構造の変更コマンド|ビューの変更コマンド|ウィンドウの移動コマンド|  
|マウスコマンド|ポップアップコマンドの移動|MROW () 関数|  
|MRKBAR () 関数|MRKPAD () 関数||  
|MWINDOW () 関数|MDOWN () 関数||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NUMLOCK () 関数|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OBJNUM () 関数|OBJTOCLIENT () 関数|横棒コマンド|  
|OEMTOANSI () 関数|ON APLABOUT コマンド|[終了時] メニューコマンド|  
|ON ESCAPE コマンド|終了バーコマンドで|ON KEY = コマンド|  
|ON EXIT PAD コマンド|ON EXIT ポップアップコマンド|ON PAD コマンド|  
|キーラベルのコマンド|ON MACHELP コマンド|選択バーのコマンド|  
|ON PAGE コマンド|ON READERROR コマンド|ON SELECTION ポップアップコマンド|  
|[選択範囲] メニューコマンド|ON SELECTION PAD コマンド||  
|ON SHUTDOWN コマンド|OBJVAR () 関数||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|_PADVANCE システムメモリ変数|_PAGENO システムメモリ変数|_PBPAGE システムメモリ変数|  
|_PCOLNO システムメモリ変数|_PCOPIES システムメモリ変数|_PDRIVER システムメモリ変数|  
|_PDSETUP システムメモリ変数|_PECODE システムメモリ変数|_PEJECT システムメモリ変数|  
|_PEPAGE システムメモリ変数|_PLENGTH システムメモリ変数|_PLINENO システムメモリ変数|  
|_PLOFFSET システムメモリ変数|_PPITCH システムメモリ変数|_PQUALITY システムメモリ変数|  
|_PRETEXT システムメモリ変数|_PSCODE システムメモリ変数|_PSPACING システムメモリ変数|  
|_PWAIT システムメモリ変数|PACK データベースコマンド|PAD () 関数|  
|PCOL () 関数|PEMSTATUS () 関数|PLAY マクロコマンド|  
|POP キーコマンド|ポップアップメニューコマンド|POP ポップアップコマンド|  
|POPUP () 関数|PRINTJOB ...ENDPRINTJOB コマンド|PRINTSTATUS () 関数|  
|PRMBAR () 関数|PRMPAD () 関数|PROMPT () 関数|  
|PROW () 関数|PRTINFO () 関数|キーのプッシュコマンド|  
|プッシュメニューコマンド|プッシュポップアップコマンド|PUTFILE () 関数|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|QUIT コマンド|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|_RMARGIN システムメモリ変数|RD コマンド|READKEY () 関数|  
|READ コマンド|メニューコマンドの読み取り|RELEASE BAR コマンド|  
|REFRESH () 関数|REINDEX コマンド|リリースライブラリコマンド|  
|RELEASE CLASSLIB コマンド|RELEASE コマンド|リリースパッドコマンド|  
|リリースメニューコマンド|RELEASE MODULE コマンド|WINDOWS コマンドのリリース|  
|リリースポップアップコマンド|リリースプロシージャコマンド|RENAME コマンド|  
|クラスの削除コマンド|クラス名の変更コマンド|ビュー名の変更コマンド|  
|接続の名前の変更コマンド|テーブル名の変更コマンド|RESTORE FROM コマンド|  
|レポートコマンド|REQUERY () 関数|ウィンドウの復元コマンド|  
|マクロの復元コマンド|RESTORE SCREEN コマンド|RGBSCHEME () 関数|  
|RESUME コマンド|RGB () 関数|&#124; を実行します。 コマンド|  
|RMDIR コマンド|ROW () 関数||  
|RUNSCRIPT コマンド|RDLEVEL () 関数||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|マクロの保存コマンド|画面の保存コマンド|コマンドの保存|  
|WINDOWS コマンドの保存|SCHEME () 関数|SCOLS () 関数|  
|SCROLL コマンド|_SCREEN システムメモリ変数|SET コマンド|  
|代替コマンドの設定|SET ANSI コマンド|SET APLABOUT コマンド|  
|自動保存コマンドの設定|SET BELL コマンド|点滅コマンドの設定|  
|罫線の設定コマンド|BRSTATUS コマンドの設定|SET CLASSLIB コマンド|  
|CLEAR コマンドの設定|時計の設定コマンド|コマンドの色の設定|  
|SCHEME コマンドの色を設定する|カラーセットの設定コマンド|色をコマンドに設定|  
|互換性のあるコマンドの設定|CONFIRM コマンドの設定|コンソールコマンドの設定|  
|CPCOMPILE の設定|CPDIALOG の設定|通貨の設定コマンド|  
|カーソルの設定コマンド|DATASESSION コマンドの設定|デバッグコマンドの設定|  
|10進数の設定コマンド|区切り記号の設定コマンド|開発コマンドの設定|  
|デバイスコマンドの設定|DISPLAY コマンドの設定|DOHISTORY コマンドの設定|  
|ECHO コマンドの設定|SET ESCAPE コマンド|フォーマットの設定コマンド|  
|関数の設定コマンド|見出しの設定コマンド|ヘルプコマンドの設定|  
|HELPFILTER コマンドの設定|濃度の設定コマンド|キーの設定コマンド|  
|SET KEYCOMP コマンド|LOGERRORS の設定コマンド|MACDESKTOP コマンドの設定|  
|SET MACHELP コマンド|SET MACKEY コマンド|余白の設定コマンド|  
|コマンドのマークの設定|マークをコマンドに設定|MEMOWIDTH コマンドの設定|  
|メッセージの設定コマンド|マウスの設定コマンド|SET 走行距離計コマンド|  
|SET OLEOBJECT コマンド|パレットの設定コマンド|SET PDSETUP コマンド|  
|SET POINT コマンド|プリンターコマンドの設定|READBORDER コマンドの設定|  
|更新コマンドの設定|リソースの設定コマンド|安全性の設定コマンド|  
|スコアボードコマンドの設定|秒の設定コマンド|区切り記号の設定コマンド|  
|影の設定コマンド|コマンドのスキップの設定|領域の設定コマンド|  
|SET STATUS コマンド|ステータスバーの設定コマンド|ステップの設定コマンド|  
|固定コマンドの設定|SYSFORMATS の設定コマンド|SYSMENU コマンドの設定|  
|トークコマンドの設定|TEXTMERGE コマンドの設定|TEXTMERGE の区切り記号の設定コマンド|  
|トピックの設定コマンド|トピック ID の設定コマンド|TRBETWEEN コマンドの設定|  
|SET 先行入力コマンド|ビューの設定コマンド|メモコマンドの設定ウィンドウ|  
|XCMDFILE コマンドの設定|_SHELL システムメモリ変数|GET コマンドを表示する|  
|SHOW コマンド|メニューコマンドの表示|オブジェクトコマンドの表示|  
|ポップアップコマンドの表示|[ウィンドウの表示] コマンド|サイズポップアップコマンド|  
|ウィンドウのサイズ変更コマンド|SKPBAR () 関数|SKPPAD () 関数|  
|SOUNDEX () 関数|_SPELLCHK システムメモリ変数|SQL 関数|  
|SROWS () 関数|_STARTUP システムメモリ変数|中断コマンド|  
|Sys () を除く sys () 関数 (2011)|SYSMETRIC () 関数||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TABS システムメモリ変数|テキスト...ENDTEXT コマンド|TXTWIDTH () 関数|  
|TRANSFORM () 関数|_TRANSPORT システムメモリ変数||  
|TYPE コマンド|_THROTTLE システムメモリ変数||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|UPDATED () 関数|コマンドを使用する||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|データベースの検証コマンド|VARREAD () 関数|VERSION () 関数|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|_WINDOWS システムメモリ変数|_WIZARD システムメモリ変数|WCHILD () 関数|  
|WAIT コマンド|WBORDER () 関数|WFONT () 関数|  
|WCOLS () 関数|WEXIST () 関数|WLROW () 関数|  
|使用...ENDWITH コマンド|WLAST () 関数|WONTOP () 関数|  
|WMAXIMUM () 関数|WLCOL () 関数|WREAD () 関数|  
|WOUTPUT () 関数|WMINIMUM () 関数|WVISIBLE () 関数|  
|WPARENT () 関数|WTITLE () 関数||  
|WROWS () 関数|_WRAP システムメモリ変数||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ズームウィンドウのコマンド|||
