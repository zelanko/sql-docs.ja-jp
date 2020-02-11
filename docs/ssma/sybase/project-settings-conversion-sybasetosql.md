---
title: プロジェクトの設定 (変換) (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5d4936638fc9e283caafffc2f2a7cfdbed396920
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028764"
---
# <a name="project-settings-conversion-sybasetosql"></a>プロジェクトの設定 (変換) (SybaseToSQL)
[**プロジェクトの設定**] ダイアログボックスの [変換] ページには、Ssma が Sybase Adaptive Server ENTERPRISE (ASE) 構文[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をまたは SQL Azure 構文に変換する方法をカスタマイズする設定が含まれています。  
  
[変換] ペインは、[**プロジェクトの設定**] ダイアログボックスと [**既定のプロジェクトの設定**] ダイアログボックスで使用できます。  
  
-   すべての SSMA プロジェクトの設定を指定する場合は、[**ツール**] メニューの [**既定のプロジェクト設定**] を選択し、左側のウィンドウの下部にある [**全般**] をクリックして、[**変換**] をクリックします。  
  
-   現在のプロジェクトの設定を指定するには、[**ツール**] メニューの [**プロジェクトの設定**] をクリックし、左側のウィンドウの下部にある [**全般**] をクリックして、[**変換**] をクリックします。  
  
## <a name="miscellaneous-options"></a>その他のオプション  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure と ASE では、異なるエラーコードが使用されます。  
  
この設定を使用して、ASE コード内で **@@ERROR **への参照が検出されたときに、ssma が出力またはエラー一覧ペインに表示するメッセージの種類 (警告またはエラー) を指定します。  
  
-   [変換] を選択し、[**警告付きでマーク**] を選択すると、ssma はステートメントを変換し、警告コメントでマークします。  
  
-   [**エラー付きでマーク**] を選択した場合、ssma は変換をスキップし、ステートメントにエラーコメントをマークします。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 変換して警告付きでマーク  
  
**フルモード:** エラーでマーク  
  
**LIKE 演算子の変換**  
Sybase ASE の動作に一致するように、LIKE オペランドを変換するかどうかを指定します。 ここで、Sybase は、like パターンで末尾の空白をトリミングします。 この回避策は、最大有効桁数が指定された固定長データ型に right 式をキャストすることです。  
  
-   式を修正せずに変換するには、[**単純変換**] を選択します。  
  
-   ASE の動作を使用するには、[**固定長にキャスト**] を選択します。  
  
[モード] ボックスで変換モードを選択すると、SSMA によって次の設定が適用されます。  
  
**既定/オプティミスティックモード**: 単純変換  
  
**Full モード**: 固定長にキャスト  
  
**空の文字列を数値型に変換またはキャストする**  
Numeric 型を datatype 引数として使用して、変換またはキャスト式内の空の文字列または空の文字列を処理する方法を指定します。 この設定では、次のオプションを使用できます。  
  
-   式を修正せずに変換するには、[**単純変換**] を選択します。  
  
-   **空の文字列を0として**指定した場合、文字列パラメーター {s} は case ltrim (rtrim ({s})) に置き換えられ、"" の後に 0 else {s} が終了します。  
  
[モード] ボックスで変換モードを選択すると、SSMA によって次の設定が適用されます。  
  
**既定/オプティミスティックモード**: 単純変換  
  
**フルモード**: 空の文字列を0として指定します。  
  
**NULL の連結**  
この設定では、文字列の連結を NULL に変換する方法を指定します。 この特定の設定には、次のオプションを設定できます。  
  
-   **ISNULL 関数で Wrap:** このオプションを設定すると、連結内のすべての非定数 ' string_expression ' は ISNULL (string_expression) でラップされ、Null は空の文字列に置き換えられます。  
  
-   **現在の構文を保持する**  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 現在の構文を保持する  
  
**フルモード:** ISNULL 関数を使用した Wrap  
  
**空の文字列の変換**  
この設定では、空の文字列を変換する方法を指定します。 この特定の設定には、次のオプションを設定できます。  
  
-   **すべての文字列式をスペースで置換する**  
  
-   **空の文字列定数をスペースで置換する**  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure 動作を使用するには、[**現在の構文を保持**する] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 現在の構文を保持する  
  
**フルモード:** すべての文字列式をスペースで置換する  
  
**変換し、バイナリ文字列変換をキャストする**  
バイナリ値を数値に変換すると、異なるプラットフォームで異なる値が返される場合があります。 たとえば、x86 プロセッサでは、CONVERT (integer, 0x00000100) は ASE と256の65536を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返します。 ASE では、バイトの順序によって異なる値も返されます。  
  
この設定を使用して、SSMA がバイナリ値を含む CONVERT および CASE 式を変換する方法を制御します。  
  
-   警告や修正を行わずに式を変換するには、[**単純変換**] を選択します。 ASE サーバーにバイナリ値の変更を必要としないバイト順があることがわかっている場合は、この設定を使用します。  
  
-   SSMA 変換を行い、で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用する式を修正するには、[**変換と修正**] を選択します。 リテラル定数内のバイト順序は逆になります。 その他のバイナリ値 (バイナリ変数や列など) には、エラーが表示されます。 ASE サーバーにバイナリ値の変更を必要とするバイト順があることがわかっている場合は、この値を使用します。  
  
-   SSMA で式を変換して修正するには、[変換] を選択して [**警告付き**] を選択し、変換されたすべての式を警告コメントでマークします。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定のモード:** 変換して警告付きでマーク  
  
**オプティミスティックモード:** 単純な変換  
  
**フルモード:** 変換と修正  
  
**動的 SQL**  
この設定を使用して、ASE コードで動的 SQL が検出されたときに、SSMA が出力またはエラー一覧ペインに表示するメッセージの種類 (警告またはエラー) を指定します。  
  
-   [変換] を選択し、**警告付きでマーク**すると、ssma は動的 SQL を変換し、ステートメントに警告コメントをマークします。  
  
-   [**エラー付きでマーク**] を選択した場合、ssma は変換をスキップし、ステートメントにエラーコメントをマークします。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 変換して警告付きでマーク  
  
**フルモード:** エラーでマーク  
  
**等値チェックの変換**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure では、ANSI_NULLS 設定が on の場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、等値比較に null 値が含まれている場合、/SQL Azure は不明な値を返します。 ANSI_NULLS がオフの場合、null 値を含む等値比較では、比較対象の列と式、または2つの式が両方とも null の場合に true が返されます。 既定では (ANSINULL OFF) Sybase ASE 等値比較[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、ANSI_NULLS OFF を使用して/SQL Azure のように動作します。  
  
-   **単純な変換**を選択した場合、ssma は、null [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]値に対して追加のチェックを行わずに、ASE コードを/SQL Azure 構文に変換します。 この設定は、ANSI_NULLS が/SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でオフになっている場合、またはケースごとに等価比較を変更する場合に使用します。  
  
-   [ **Null 値を考慮**する] を選択した場合、ssma では、is null 句と IS not null 句を使用して null 値のチェックが追加されます。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 単純な変換  
  
**フルモード:** NULL 値を考慮する  
  
**書式指定文字列**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure では、PRINT ステートメントと RAISERROR ステートメントで*format_string*引数がサポートされなくなりました。 *Format_string*変数は、置換可能なパラメーターを文字列に直接配置し、実行時にパラメーターを置換することをサポートしています。 代わりに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、文字列リテラルまたは変数を使用して作成された文字列のいずれかを使用して、完全な文字列が必要になります。 詳細については、オンラインブックの[!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「印刷 ()」を参照してください。  
  
SSMA が*format_string*引数を検出すると、変数を使用して文字列リテラルを作成するか、新しい変数を作成し、その変数を使用して文字列を構築できます。  
  
-   PRINT 関数と RAISERROR 関数に文字列リテラルを使用するには、[**新しい文字列の作成**] を選択します。  
  
    このモードでは、PRINT ステートメントまたは RAISERROR ステートメントでプレースホルダーとローカル変数が使用されていない場合、ステートメントは変更されません。 2倍のパーセント文字 (%%)は、PRINT 文字列リテラルで1パーセント文字% に変更されます。  
  
    PRINT ステートメントまたは RAISERROR ステートメントで、次の例のように、プレースホルダーと1つ以上のローカル変数が使用されている場合。  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA は、次の構文に変換します。  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    *Format_string*が次のステートメントのような変数である場合は、次のようになります。  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA は、単純な文字列変換を行うことはできず、新しい変数を作成する必要があります。  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        CAST (@arg1 AS varchar(max)))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        CAST (@arg2 AS varchar(max)))  
    PRINT @print_format_1  
    ```  
    **Create new string** mode を使用する場合、ssma は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オプション CONCAT_NULL_YIELDS_NULL がオフであると想定しています。 そのため、SSMA は null 引数をチェックしません。  
  
-   SSMA で PRINT ステートメントと RAISERROR ステートメントごとに新しい変数を作成し、その変数を文字列値として使用するには、[**新しい変数の作成**] を選択します。  
  
    このモードでは、PRINT ステートメントまたは RAISERROR ステートメントでプレースホルダーとローカル変数が使用されていない場合、SSMA は、すべての二重パーセント文字 (%%) を置き換えます。/SQL Azure 構文に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]準拠するには、1パーセントの文字を使用します。  
  
    PRINT ステートメントまたは RAISERROR ステートメントで、次の例のように、プレースホルダーと1つ以上のローカル変数が使用されている場合。  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA は、次の構文に変換します。  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    *Format_string*が次のステートメントのような変数である場合は、次のようになります。  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA は、次のように新しい変数を作成し、各引数に null 値があるかどうかをチェックします。  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@arg1 AS varchar(max)),''))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        ISNULL(CAST (@arg2 AS varchar(max)),''))  
    PRINT @print_format_1  
    ```  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 新しい文字列の作成  
  
**フルモード:** 新しい変数の作成  
  
**Timestamp 列に明示的な値を挿入する**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure では、timestamp 列への明示的な値の挿入はサポートされていません。  
  
-   Timestamp 列を INSERT ステートメントから除外するには、[**列を除外**する] を選択します。  
  
-   Timestamp 列が INSERT ステートメントに含まれるたびにエラーメッセージを出力するには、[**エラーのあるマーク**] を選択します。 このモードでは、INSERT ステートメントは変換されず、エラーコメントでマークされます。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 列の除外  
  
**フルモード:** エラーでマーク  
  
**プロシージャで定義されている一時オブジェクトを格納する**  
この設定は、プロシージャに表示される一時オブジェクトの定義を変換時にソースメタデータに格納するかどうかを指定します。  
  
-   メタデータに格納する場合は、[**はい]** を選択します。  
  
-   オブジェクトを保存する必要がない場合は、[**いいえ**] を選択します。  
  
**既定/オプティミスティックモード:** うん  
  
**フルモード:** 違います  
  
**プロキシテーブルの変換**  
ASE プロキシテーブルをテーブルに変換する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]か SQL Azure テーブルに変換するかを指定します。変換されていない場合は、コードがエラーコメントでマークされます。  
  
-   [**変換**] を選択して、プロキシテーブルを通常のテーブルに変換します。  
  
-   プロキシテーブルコードをエラーコメントでマークするだけの場合は、[**エラー付きでマーク**] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティック/フルモード:** エラーでマーク  
  
**RAISERROR base メッセージ番号**  
ASE ユーザーメッセージは、各データベースに格納されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーメッセージは一元的に格納され、 **sys. messages**カタログビューを介して使用できるようになります。 さらに、ASE ユーザーメッセージは2万から開始[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されますが、エラーメッセージは50001から開始されます。  
  
この設定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーメッセージに変換するために ASE ユーザーメッセージ番号に追加する番号を指定します。 が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **システム**カタログビューにユーザーメッセージを持っている場合は、この数をより大きな値に変更することが必要になる場合があります。 これは、変換されたメッセージ番号が既存のメッセージ番号と競合しないようにするためです。  
  
次のことを考慮してください。  
  
-   17000-19999 の範囲の ASE メッセージは、sysmessages システムテーブルからのものであり、変換されません。  
  
-   RAISERROR ステートメントで参照されているメッセージ番号が定数である場合、SSMA は、新しいユーザーメッセージ番号を決定するために、基本メッセージ番号を定数に追加します。  
  
-   参照されるメッセージ番号が変数または式である場合は、SSMA によって中間のローカル変数が作成されます。  
  
-   オプティミスティックモードでは、SSMA は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オプション CONCAT_NULL_YIELDS_NULL がオフであり、NULL 引数のチェックを行わないことを前提としています。  
  
-   フルモードでは、SSMA が null 引数をチェックします。  
  
-   RAISERROR WITH ERRORDATA *list*は変換されません。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティック/Full モード:** 30001  
  
**システム オブジェクト**  
この設定を使用して、ASE システムオブジェクトの使用が検出されたときに [出力] ペインまたは [エラー一覧] ペインに表示されるメッセージの種類 (警告またはエラー) を指定します。  
  
-   [変換] を選択し、[**警告付きでマーク**] を選択した場合、ssma は参照をシステムオブジェクトに変換し、警告コメント付きのステートメントをマークします。  
  
-   [**エラー付きでマーク**] を選択した場合、ssma はシステムオブジェクトへの参照を変換せず、ステートメントにエラーコメントをマークします。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 変換して警告付きでマーク  
  
**フルモード:** エラーでマーク  
  
**未解決の識別子**  
この設定を使用すると、[出力] ペインまたは [エラー一覧] ウィンドウで識別子を解決できないときに表示されるメッセージの種類 (警告またはエラー) を指定できます。  
  
-   [変換] を選択し、[**警告付きでマーク**する] を選択すると、ssma は参照を未解決の識別子に変換しようとし、警告コメント付きのステートメントをマークします。  
  
-   [**エラー付きでマーク**] を選択した場合、ssma は参照を未解決の識別子に変換せず、ステートメントにエラーコメントをマークします。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 変換して警告付きでマーク  
  
**フルモード:** エラーでマーク  
  
## <a name="system-function-options"></a>システム関数のオプション  
**CHARINDEX 関数**  
ASE では、CHARINDEX は、すべての入力式が NULL の場合にのみ NULL を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure は、入力式が NULL の場合は NULL を返します。  
  
-   ASE の動作を使用するには、[**置換関数**] を選択します。 CHARINDEX 関数のすべての呼び出しは、Sybase ASE の動作をエミュレートするために渡されたパラメーターの型 (スキーマ名の2つの下のユーザーデータベースで作成された) に基づいて、CHARINDEX_VARCHAR または CHARINDEX_NVARCHAR のユーザー定義関数の呼び出しに置き換えられます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure 動作を使用するには、[**現在の構文を保持**する] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 現在の構文を保持する  
  
**フルモード:** Replace 関数  
  
**DATALENGTH 関数**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure と ASE は、値が単一の空白である場合に、DATALENGTH 関数によって返される値と異なります。 この場合、/ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure は0を返し、ASE は1を返します。  
  
-   ASE の動作を使用するには、[**置換関数**] を選択します。 DATALENGTH 関数のすべての呼び出しは、Sybase ASE の動作をエミュレートするために CASE 式と置き換えられます。  
  
-   既定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure の動作を使用するには、[**現在の構文を保持**する] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 現在の構文を保持する  
  
**フルモード:** Replace 関数  
  
**INDEX_COL 関数**  
ASE は、INDEX_COL 関数に対して省略可能な*user_id*引数をサポートしています。ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure はこの引数をサポートしていません。 *User_id*引数を使用した場合、この関数を/SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]構文に変換することはできません。  
  
-   ASE の動作を使用するには、[**関数の変換**] を選択します。 コードに*user_id*引数が含まれている場合は、ssma によってエラーが表示されます。  
  
-   INDEX_COL が発生するたびにエラーメッセージを表示するには、[**エラー付きでマーク**] を選択します。 SSMA は参照を関数に変換せず、ステートメントにエラーコメントをマークします。  
  
**既定/オプティミスティック/フルモード:** エラーでマーク  
  
**INDEX_COLORDER 関数**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure に INDEX_COLORDER システム関数がありません。  
  
-   ASE の動作を使用するには、[**関数の変換**] を選択します。 INDEX_COLORDER 関数へのすべての呼び出しは、Sybase ASE の動作をエミュレートする同じ名前のユーザー定義関数 (スキーマ名の2ss の下にあるユーザーデータベースで作成された名前 INDEX_COLORDER) の呼び出しに置き換えられます。  
  
-   INDEX_COLORDER が検出されるたびにエラーメッセージを表示するには、[**エラー付きでマーク**] を選択します。 SSMA は参照を関数に変換せず、ステートメントにエラーコメントをマークします。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティック/フルモード:** エラーでマーク  
  
**LEFT および RIGHT 関数**  
Sybase の左および右の関数の動作は、負の長さのパラメーターによって異なります。  
  
-   ASE の動作を使用するには、[**置換関数**] を選択します。 長さのパラメーターは、負の値に対して null を返す CASE 式で置き換えられます。  
  
-   SQL Server の動作を使用するには、[**現在の構文を保持**する] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 現在の構文を保持する  
  
**フルモード:** Replace 関数  
  
> [!NOTE]  
> 長さのパラメーターがリテラル値であり、複雑な式ではない場合は、プロジェクトの設定に関係なく、長さの値は常に null に置き換えられます。  
  
**NEXT_IDENTITY 関数**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure に NEXT_IDENTITY システム関数がありません。  
  
-   ASE の動作を使用するには、[**関数の変換**] を選択します。 NEXT_IDENTITY 関数のすべての呼び出しは、Sybase ASE の動作をエミュレートする式 (IDENT_CURRENT (パラメーター値) + IDENT_INCR (パラメーター値) に置き換えられます。  
  
-   NEXT_IDENTITY が検出されるたびにエラーメッセージを表示するには、[**エラー付きでマーク**] を選択します。 SSMA は参照を関数に変換せず、ステートメントにエラーコメントをマークします。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティック/フルモード:** エラーでマーク  
  
**PATINDEX 関数**  
Sybase ASE の動作に一致するように PATINDEX 関数を変換するかどうかを指定します。 ここで、Sybase は検索パターンで末尾の空白をトリミングします。 回避策として、最大有効桁数を持つ固定長データ型に値式のキャストを作成し、rtrim 関数を検索パターンに適用します。  
  
-   ASE の動作を使用するには、[**使用**] を選択します。  
  
-   既定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure の動作を使用するには、[**使用しない**] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 使用しない  
  
**フルモード:** 使用  
  
**REPLICATE 関数**  
REPLICATE 関数は、指定された回数だけ文字列を繰り返します。 ASE では、文字列を0回繰り返すように指定した場合、結果は null になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure の場合、結果は空の文字列になります。  
  
-   ASE の動作を使用するには、[**置換関数**] を選択します。 レプリケート関数のすべての呼び出しは、Sybase ASE の動作をエミュレートするために渡されたパラメーターの型 (スキーマ名の2つの下のユーザーデータベースで作成された) に基づいて、REPLICATE_VARCHAR または REPLICATE_NVARCHAR ユーザー定義関数の呼び出しに置き換えられます。  
  
-   既定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure の動作を使用するには、[**置換関数**] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード/フルモード:** Replace 関数  
  
**TRIM (LTRIM, RTRIM) 関数**  
この設定では、Trim (LTRIM, RTRIM) 関数の呼び出しを Sybase ASE に相当する構文関数と置き換えるか、現在の構文を保持するかを指定します。 この特定の設定には、次のオプションがあります。  
  
-   **Replace 関数**  
  
-   **現在の構文を保持する**  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード/フルモード:** Replace 関数  
  
**SUBSTRING 関数**  
ASE では、式`SUBSTRING(expression, start, length)`の中の文字数よりも大きい値が指定されている場合、または長さが0の場合、関数は NULL を返します。 / [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure では、同等の式は空の文字列を返します。  
  
-   ASE の動作を使用するには、[**置換関数**] を選択します。 SUBSTRING 関数のすべての呼び出しは、SUBSTRING_VARCHAR または SUBSTRING_NVARCHAR または SUBSTRING_VARBINARY ユーザー定義関数の呼び出しに置き換えられます。これは、渡されたパラメーターの型 (スキーマ名の2つの下のユーザーデータベースで作成) に基づいて、Sybase ASE の動作。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure 動作を使用するには、[**現在の構文を保持**する] を選択します。  
  
[**モード**] ボックスで変換モードを選択すると、ssma によって次の設定が適用されます。  
  
**既定/オプティミスティックモード:** 現在の構文を保持する  
  
**フルモード:** Replace 関数  
  
## <a name="tables"></a>TABLES  
**主キーの追加**  
アクセステーブルに主キーまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一意のインデックスがない場合は、テーブルまたは SQL Azure テーブルに新しい主キーを作成します。  
  
-   **既定のモード**: False  
  
-   **オプティミスティックモード**: False  
  
-   **フルモード**: True  
  
> [!NOTE]  
> SQL Azure に接続されている場合は、既定で True に設定されます。  
  
## <a name="see-also"></a>参照  
[ユーザーインターフェイスリファレンス &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  
