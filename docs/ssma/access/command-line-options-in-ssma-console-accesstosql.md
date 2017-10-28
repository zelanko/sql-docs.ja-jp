---
title: "SSMA コンソール (AccessToSQL) でのコマンド ライン オプション |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 80642503480add90fc75573338760ab86139694c
ms.openlocfilehash: 827257d90042aa1655545edd9fc20d114952f426
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>SSMA コンソール (AccessToSQL) でのコマンド ライン オプション
Microsoft は、堅牢な一連の実行および SSMA アクティビティを制御するコマンド ライン オプションを提供します。 次のセクションでは、追加の詳細情報を提供します。  
  
## <a name="command-line-options-in-the-ssma-console"></a>SSMA コンソールのコマンド ライン オプション  
コンソールは、コマンドのオプションは、ドキュメントに記載します。  
  
このセクションの目的で用語 'option' とも呼びます 'switch' です。  
  
オプションは、小文字は区別されず、いずれかで始めることは、'**-**'または'**/**' 文字です。  
  
オプションを指定する場合は必須では、対応するオプション パラメーターを指定することです。  
  
オプション パラメーターは、オプションの文字から空白の領域で区切る必要があります。  
  
**構文例:**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
二重引用符で囲まれた空白を含むフォルダーまたはファイルの名前を指定する必要があります。  
  
コマンドラインの入力とエラー メッセージの出力は STDOUT にまたは指定されたファイル内に格納されます。  
  
### <a name="script-file-option-sscript"></a>ファイルのオプションのスクリプト: – s/スクリプト  
必須のスイッチでは、スクリプト ファイルのパスと名前は、SSMA によって実行されるコマンドのシーケンスのスクリプトを指定します。  
  
**構文例:**  
  
`C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>変数の値のファイル オプション: – v/変数  
変数の値のファイルには、スクリプト ファイルで使用される変数が構成されています。 スイッチは省略できます。 変数がない変数ファイルで宣言されているし、スクリプト ファイルで使用される、アプリケーションが、エラーが発生し、コンソールの実行を終了します。  
  
**構文例:**  
  
-   変数は、おそらく 1 つで、既定値と別に該当する場合は、インスタンス固有の値の複数の変数値ファイルで定義されています。 変数の重複がある場合に、コマンドラインの引数で指定された最後の変数ファイルは、基本設定を受け取る。  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>サーバー接続のファイル オプション: serverconnection/– c  
このファイルには、各サーバーのサーバー接続情報が含まれています。 各サーバーの定義は、id。 一意なサーバーによって識別されます。 サーバーの Id は、接続に関連するコマンドのスクリプト ファイルで参照されます。  
  
サーバーの定義は、サーバー接続のファイルやスクリプト ファイルの一部にすることができます。 スクリプト ファイル内のサーバー id は、サーバー接続ファイルに優先されるサーバー id の重複がある場合にします。  
  
**構文例:**  
  
-   サーバーの Id は、スクリプト ファイルで使用されます。 別のサーバー接続ファイルで定義されています。 このファイルには、変数値ファイルで定義されている変数が使用されます。  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   サーバーの定義がスクリプト ファイルに埋め込まれます。  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML の出力オプション:-x/xmloutput [xmloutputfile]  
このコマンドはコンソールにするか、xml ファイルを xml 形式でコマンドの出力メッセージを出力するために使用されます。  
  
2 つのオプションあります xmloutput、つまり。  
  
-   Xmloutput スイッチの後にファイル パスを指定する場合は、ファイルに出力がリダイレクトされます。  
  
    **構文例:**  
  
    `C:\>SSMAforAccessConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Xmloutput スイッチの後にファイル パスが指定されていない場合は、コンソール自体に、xmlout が表示されます。  
  
    **構文例:**  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>ログ ファイルのオプション: – l/ログ  
コンソール アプリケーションでのすべての SSMA 操作は、ログ ファイルに記録され、スイッチは省略可能です。 ログ ファイルとそのパスをコマンドラインで指定する場合、ログが指定された場所に生成を取得します。 それ以外の場合、これは既定の場所で生成されたを取得します。  
  
**構文例:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>プロジェクトの環境のフォルダー オプション: – e/projectenvironment  
このオプションのスイッチは、環境設定のプロジェクト フォルダーに現在の SSMA プロジェクトを表します。  
  
**構文例:**  
  
`C:\>SSMAforAccessConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option-psecurepassword"></a>Password オプションをセキュリティで保護された: – p/securepassword  
このオプションでは、サーバー接続の暗号化されたパスワードを指定します。 移行プロジェクトで使用するサーバー接続のパスワードの暗号化を管理できるため、任意のスクリプトを実行したり、任意の移行関連のアクティビティでは、ヘルプしないその他のすべてのオプションとは異なります。  
  
コマンド ライン パラメーターとして、他のオプションやパスワードを入力することはできません。 それ以外の場合、エラーが発生します。 詳細については、次を参照してください。、[管理パスワード](http://msdn.microsoft.com/b099d0f9-dd37-4c87-8b6f-ed0177881ea4)セクションです。  
  
次のサブオプションがサポートされて`–p/securepassword`:  
  
-   パスワードを追加または既存のパスワードを指定したサーバー ID に対して、またはサーバー接続ファイルで定義されているすべてのサーバー Id の保護された記憶域に更新します。  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   指定したサーバー ID のまたはすべてのサーバー Id の保護された記憶域から暗号化されたパスワードを削除します。  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   パスワードの暗号化をサーバー Id の一覧を表示するには。  
  
    `–p/securepassword –l/list`  
  
-   暗号化されたファイルを保護されたストレージに格納されているパスワードをエクスポートします。 このファイルは、パス フレーズをユーザー指定で暗号化されます。  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   暗号化、以前エクスポートされたファイルが、ユーザーが指定したパスフレーズを使用してローカルの保護されたストレージにインポートされます。 ファイルが暗号化解除は、さらに、ローカル コンピューターの暗号化は、新しいファイルに格納されます。  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    コンマ区切り記号を使用して、複数のサーバー Id を指定できます。  
  
### <a name="help-option-help"></a>Help オプション: –?/help  
SSMA コンソールのオプションの構文の概要が表示されます。  
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
SSMA コンソールのコマンド ライン オプションの表形式の表示を参照してください[付録 - 1 & #40 です。AccessToSQL &#41;](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>SecurePassword ヘルプ オプション: – securepassword-?/help  
SSMA コンソールのオプションの構文の概要が表示されます。  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
SSMA コンソールのコマンド ライン オプションの表形式の表示を参照してください[付録 - 1 & #40 です。AccessToSQL &#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>次の手順  
次の手順は、プロジェクトの要件によって異なります。  
  
1.  パスワードまたはエクスポートを指定する/パスワードのインポートを参照してください[パスワードの管理 & #40 です。AccessToSQL &#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  レポートの生成に、次を参照してください。[レポートの生成 & #40 です。AccessToSQL &#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  コンソールで問題をトラブルシューティングするには、次を参照してください。[トラブルシューティング & #40 です。AccessToSQL &#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  

