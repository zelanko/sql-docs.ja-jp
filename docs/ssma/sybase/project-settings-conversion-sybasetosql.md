---
title: "プロジェクトの設定 (変換) (SybaseToSQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8e49acca5ae556f6f892c364a7bd81d0db4c68ec
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-conversion-sybasetosql"></a>プロジェクトの設定 (変換) (SybaseToSQL)
[変換] ページ、**プロジェクト設定** ダイアログ ボックスには、SSMA を Sybase Adaptive Server Enterprise (ASE) 構文に変換する方法をカスタマイズする設定が含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文。  
  
変換ウィンドウがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   すべての SSMA プロジェクトの設定を指定するかどうか、**ツール**メニューの [**プロジェクト設定の既定の**、] をクリックして**全般**クリックして、左側のウィンドウの下部にある**変換**です。  
  
-   現在のプロジェクトの設定を指定する、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックして、左側のウィンドウの下部にある**変換**です。  
  
## <a name="miscellaneous-options"></a>その他のオプション  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure と ASE、別のエラー コードを使用します。  
  
参照を検出したときに、SSMA が出力またはエラー一覧 ペインに表示されるメッセージ (警告またはエラー) の種類を指定するこの設定を使用して**@@ERROR**  ASE コードにします。  
  
-   選択した場合**変換し、警告マーク**SSMA は、ステートメントに変換され、警告のコメントでマークを付けます。  
  
-   選択した場合**エラーでマーク**SSMA は変換をスキップし、エラーのコメント ステートメントをマークします。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**変換し、警告マーク  
  
**フル モード:**エラーでマーク  
  
**LIKE 演算子の変換**  
Sybase ASE 動作と一致するオペランドと同様に変換するかどうかを指定します。 Sybase が like パターンの末尾の空白をトリミングすることです。 回避策では、最大有効桁数を持つ固定長データ型に右の式のキャストを作成します。  
  
-   選択**単純変換**修正なしの式に変換します。  
  
-   ASE 動作の選択を使用する**固定長にキャストします。**  
  
[モード] ボックスの変換モードを選択するときに SSMA は、次の設定を適用します。  
  
**既定/Optimistic モード**: 単純な変換  
  
**Full モード**: 固定長にキャスト  
  
**変換するか、空の文字列を数値型のキャスト**  
データ型の引数として数値型に変換またはキャストの式内で空または空白の文字列を処理する方法を指定します。 次のオプションは、この設定に使用されます。  
  
-   選択**単純変換**修正なしの式に変換します。  
  
-   場合**空の文字列として 0 数値**が選択されている場合は、文字列パラメーター {s} は case ltrim(rtrim({s})) に置き換えられますし、ときに""0 else {s} END 式  
  
[モード] ボックスの変換モードを選択するときに SSMA は、次の設定を適用します。  
  
**既定/Optimistic モード**: 単純な変換  
  
**Full モード**: 空の文字列として 0 数値  
  
**NULL の連結**  
この設定は、文字列の連結で NULL に変換する方法を指定します。 この特定の設定には、次のオプションを設定できます。  
  
-   **ISNULL 関数でラップ:**かどうかは、このオプションが設定されている ISNULL(string_expression) ですべての非定数の連結で ' string_expression' をラップするは、null 値は空の文字列に置き換えられます。  
  
-   **現在の構文を保持します。**  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**現在の構文を保持  
  
**フル モード:** ISNULL 関数でラップ  
  
**空の文字列変換**  
この設定は、空の文字列に変換する方法を指定します。 この特定の設定には、次のオプションを設定できます。  
  
-   **領域を持つすべての文字列式を置換します。**  
  
-   **空の文字列定数をスペースに置き換えます**  
  
-   使用する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 動作**現在の構文を保持**です。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**現在の構文を保持  
  
**フル モード:**領域を持つすべての文字列式を置換  
  
**変換とキャストのバイナリ文字列変換**  
バイナリ値の数値への変換は、さまざまなプラットフォームで異なる値を返すことができます。 たとえば、x86 のプロセッサ、変換 (整数、0x00000100) を返します 65536 ASE 内およびで 256[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 ASE には、バイト順序に応じて異なる値も返されます。  
  
この SSMA 変換の変換を制御する設定とをバイナリ値を含むケースの式を使用します。  
  
-   選択**単純変換**警告または修正を行わなくても、式に変換します。 ASE サーバーが、バイナリ値の変更が不要なバイト順を持っていることがわかっている場合は、この設定を使用します。  
  
-   選択**変換し、修正**SSMA 変換しで使用する式を修正して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 リテラル定数でバイト順は反転されます。 その他のすべてのバイナリ値 (など、バイナリの変数および列) は、エラーがマークされます。 ASE サーバーが、バイナリ値に変更が必要なバイト順を持っていることがわかっている場合は、この値を使用します。  
  
-   選択**変換し、警告マーク**SSMA 変換、式を訂正してマークを付けますが、警告のコメントを含む式を変換します。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定のモード:**変換し、警告マーク  
  
**オプティミスティック モード:**単純変換  
  
**フル モード:**変換し、修正  
  
**動的 SQL**  
この設定を使用すると、ASE コードで動的な SQL を検出したときに、SSMA が出力またはエラー一覧 ペインに表示されるメッセージ (警告またはエラー) の種類を指定します。  
  
-   選択した場合**変換し、警告マーク**SSMA が動的 SQL に変換され、ステートメントと警告のコメントをマークします。  
  
-   選択した場合**エラーでマーク**SSMA は変換をスキップし、エラーのコメント ステートメントをマークします。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**変換し、警告マーク  
  
**フル モード:**エラーでマーク  
  
**等しいかどうかチェック変換**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/場合は、ANSI_NULLS の設定では、SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/等値比較に null 値が含まれている場合、SQL Azure は UNKNOWN を返します。 ANSI_NULLS がの場合は、null 値が格納された等価比較 true を返します比較対象の列と式、または 2 つの式の両方が null です。 同様に動作する比較 (ANSINULL OFF) の既定 Sybase ASE 等値による[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ANSI_NULLS OFF を使用した SQL Azure です。  
  
-   選択した場合**単純変換**、SSMA は、ASE コード変換を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/、null 値に余分なチェックなしの SQL Azure 構文です。 ANSI_NULLS がの場合、この設定を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure またはケースごとに等値比較を編集するかどうか。  
  
-   選択した場合**NULL 検討値**SSMA は、IS NULL と IS NOT NULL 句を使用して null 値のチェックを追加します。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**単純変換  
  
**フル モード:**検討する NULL 値  
  
**書式指定文字列**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure をサポートしていません、 *format_string* PRINT ステートメントおよび RAISERROR ステートメントの引数。 *Format_string*文字列に直接置き換え可能パラメーターを設定し、実行時にパラメーターを置換変数がサポートされています。 代わりに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]文字列リテラル、または変数を使用して構築された文字列を使用して、完全な文字列が必要です。 詳細については、次を参照してください。、"印刷 ([!INCLUDE[tsql](../../includes/tsql_md.md)])」の「[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
SSMA を検出した場合、 *format_string*引数か、変数を使用してリテラル文字列を作成または新しい変数を作成してその変数を使用して文字列を作成します。  
  
-   印刷と RAISERROR の関数の文字列リテラルを使用する選択**新しい文字列を作成して**です。  
  
    このモードではプレース ホルダー、およびローカル変数、PRINT または RAISERROR ステートメントを使用しない場合、ステートメントは変更されません。 二重パーセント文字 (%) は、印刷の文字列リテラルで 1 つのパーセント記号 % に変更されます。  
  
    PRINT または RAISERROR ステートメントのプレース ホルダーと 1 つを使用する場合または複数のローカル変数、次の例のようにします。  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA を次の構文に変換されます。  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    場合*format_string*など、変数を次のステートメントでは。  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA は、単純な文字列の変換を行うことはできませんし、新しい変数を作成する必要があります。  
  
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
    これを使用する場合**新しい文字列を作成**モードでは、SSMA いるものと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] CONCAT_NULL_YIELDS_NULL オプションは OFF です。 したがって、SSMA では、null 引数をチェックしません。  
  
-   SSMA 印刷と RAISERROR の各ステートメントに対して新しい変数をビルドし、文字列値をその変数を使用して、次のように選択します。**を作成する新しい変数**です。  
  
    このモードではプレース ホルダー、およびローカル変数、PRINT または RAISERROR ステートメントを使用しない場合 SSMA 文字に置き換えすべて二重パーセント (%) に準拠する 1 つのパーセント記号[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 構文です。  
  
    PRINT または RAISERROR ステートメントのプレース ホルダーと 1 つを使用する場合または複数のローカル変数、次の例のようにします。  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA を次の構文に変換されます。  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    場合*format_string*など、変数を次のステートメントでは。  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA 新しい変数を作成に次のように、各引数に null 値を確認しています。  
  
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
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**新しい文字列を作成します。  
  
**フル モード:**新しい変数を作成します。  
  
**Timestamp 列に明示的な値を挿入します。**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure では、timestamp 列に明示的な値を挿入することはできません。  
  
-   INSERT ステートメントから、timestamp 列を除外する次のように選択します。**除外列**です。  
  
-   INSERT ステートメントに timestamp 列があるたびに、エラー メッセージを印刷するには、選択**エラーでマーク**です。 このモードでは、INSERT ステートメントは変換されませんし、エラー注釈でマークされます。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:** [除外] 列  
  
**フル モード:**エラーでマーク  
  
**プロシージャで定義されている一時オブジェクトの保存**  
この設定は、変換中に、手順で表示される一時的なオブジェクトの定義を基になるメタデータに保存するかかどうかを指定します。  
  
-   選択**はい**メタデータに格納します。  
  
-   選択**いいえ**オブジェクトが格納されていない必要がある場合。  
  
**既定/オプティミスティック モード:** [はい]  
  
**フル モード:**なし  
  
**プロキシ テーブルの変換**  
ASE プロキシ テーブルに変換されますを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/または SQL Azure テーブルは変換されないと、コードのエラーのコメントが付いています。  
  
-   選択**変換**プロキシ テーブルを通常のテーブルに変換します。  
  
-   選択**エラーでマーク**単にコードをマークする、プロキシ テーブルのエラーのコメント。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic/フル モード:**エラーでマーク  
  
**RAISERROR の基本メッセージ数**  
ASE ユーザー メッセージは、各データベースに格納されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ユーザー メッセージが集中的に格納されで利用できる、 **sys.messages**カタログ ビューです。 さらに ASE ユーザー メッセージ開始 20000 が[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エラー メッセージが 50001 から開始します。  
  
この設定に変換するメッセージ番号を ASE ユーザーを追加する数を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ユーザー メッセージです。 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ユーザー メッセージを持つ、 **sys.messages**カタログ ビューでは、この番号は高い値を変更する必要があります。 これは、既存のメッセージ番号と変換後のメッセージ番号が競合しないようにします。  
  
次のことを考慮してください。  
  
-   17000 19999 の範囲内で ASE メッセージは sysmessages システム テーブルは変換されません。  
  
-   RAISERROR ステートメントで参照されているメッセージ数が、定数の場合は、SSMA は新しいユーザーのメッセージ数を決定する定数を基本メッセージ番号を追加します。  
  
-   参照されているメッセージ数が変数または式の場合は、SSMA は、中間のローカル変数を作成します。  
  
-   オプティミスティック モードでは、SSMA を想定する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] CONCAT_NULL_YIELDS_NULL オプションはオフであり、null 引数をチェックを行いません。  
  
-   フル モードでは、SSMA は、null 引数を確認します。  
  
-   RAISERROR と [エラーデータ]*リスト*は変換されません。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/オプティミスティック/全モード:** 30001  
  
**システム オブジェクト**  
この設定を使用すると、ASE システム オブジェクトの使用を検出したときに、SSMA が出力またはエラー一覧 ペインに表示されるメッセージ (警告またはエラー) の種類を指定します。  
  
-   選択した場合**変換し、警告マーク**SSMA がシステム オブジェクトへの参照を変換し、警告のコメントを付けるステートメントとしてマークされます。  
  
-   選択した場合**エラーでマーク**SSMA はシステム オブジェクトへの参照を変換しませんし、エラーのコメントを付けるステートメントとしてマークされます。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**変換し、警告マーク  
  
**フル モード:**エラーでマーク  
  
**未解決の識別子**  
この設定を使用すると、識別子を解決できない場合に、SSMA が出力またはエラー一覧 ペインに表示されるメッセージ (警告またはエラー) の種類を指定します。  
  
-   選択した場合**変換し、警告マーク**、SSMA 未解決の識別子への参照の変換を試みるし、警告のコメントを付けるステートメントとしてマークされます。  
  
-   選択した場合**エラーでマーク**SSMA は未解決の識別子への参照を変換しませんし、エラーのコメントを付けるステートメントとしてマークされます。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**変換し、警告マーク  
  
**フル モード:**エラーでマーク  
  
## <a name="system-function-options"></a>システム関数のオプション  
**CHARINDEX 関数**  
ASE のすべての入力式が NULL である場合にのみ、CHARINDEX は NULL を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または任意の入力式が NULL の場合、SQL Azure は NULL を返します。  
  
-   ASE 動作を使用するには、次のように選択します。 **Replace 関数**です。 CHARINDEX 関数へのすべての呼び出しは、(で作成したスキーマ名 's2ss' でユーザー データベース) Sybase ASE 動作をエミュレートするために渡されるパラメーターの型に基づく CHARINDEX_VARCHAR または CHARINDEX_NVARCHAR のいずれかのユーザー定義関数の呼び出しに置き換えられます。  
  
-   使用する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 動作**現在の構文を保持**です。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**現在の構文を保持  
  
**フル モード:** Replace 関数  
  
**DATALENGTH 関数**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure と ASE DATALENGTH 関数から返される値は 1 つの領域値が異なります。 この場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 0 ASE 1 を返します。  
  
-   ASE 動作を使用するには、次のように選択します。 **Replace 関数**です。 DATALENGTH 関数へのすべての呼び出しは、Sybase ASE 動作をエミュレートするために CASE 式に置き換えられます。  
  
-   既定値を使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 動作**現在の構文を保持**です。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**現在の構文を保持  
  
**フル モード:** Replace 関数  
  
**INDEX_COL 関数**  
ASE を省略可能なサポート*user_id* INDEX_COL 関数に渡す引数ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure でこの引数がサポートされていません。 使用する場合、 *user_id*引数では、この関数に変換できない[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 構文です。  
  
-   ASE 動作を使用するには、次のように選択します。 **Convert 関数**です。 コードが含まれている場合、 *user_id*引数、SSMA エラーが表示されます。  
  
-   その INDEX_COL が発生するたびに、エラー メッセージを表示する **エラーでマーク**です。 SSMA は、関数への参照は変換されませんし、エラー コメントを指定してステートメントをマークします。  
  
**既定/Optimistic/フル モード:**エラーでマーク  
  
**INDEX_COLORDER 関数**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の INDEX_COLORDER システム関数ではありません。  
  
-   ASE 動作を使用するには、次のように選択します。 **Convert 関数**です。 INDEX_COLORDER 関数へのすべての呼び出しは、同じ名前 (スキーマ名 's2ss' でユーザー データベースで作成した) Sybase ASE 動作をエミュレートする INDEX_COLORDER を持つユーザー定義関数の呼び出しに置き換えられます。  
  
-   エラー メッセージを印刷するは、その INDEX_COLORDER が発生するたびに、**エラーでマーク**です。 SSMA は、関数への参照は変換されませんし、エラー コメントを指定してステートメントをマークします。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic/フル モード:**エラーでマーク  
  
**LEFT と RIGHT 関数**  
左と右関数 Sybase 内が負の値の長さのパラメーターの動作が異なる。  
  
-   ASE 動作を使用するには、次のように選択します。 **Replace 関数**です。 長さのパラメーターは、負の値に null を返すは CASE 式には置き換えられます。  
  
-   SQL Server の動作を使用するのには、選択**現在の構文を保持**  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**現在の構文を保持  
  
**フル モード:** Replace 関数  
  
> [!NOTE]  
> 長さのパラメーターがリテラル値と、複雑な式ではない場合は、長さの値はプロジェクトの設定に関係なく、null と常に置換されます。  
  
**NEXT_IDENTITY 関数**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の NEXT_IDENTITY システム関数ではありません。  
  
-   ASE 動作を使用するには、次のように選択します。**変換関数**です。 NEXT_IDENTITY 関数へのすべての呼び出しは、式 (IDENT_CURRENT(parameter Value) + Sybase ASE 動作をエミュレートする IDENT_INCR(parameter Value) で置き換えられます  
  
-   エラー メッセージを印刷するは、その NEXT_IDENTITY が発生するたびに、**エラーでマーク**です。 SSMA は、関数への参照は変換されませんし、エラー コメントを指定してステートメントをマークします。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic/フル モード:**エラーでマーク  
  
**PATINDEX 関数**  
Sybase ASE 動作と一致する PATINDEX 関数に変換するかどうかを指定します。 Sybase が、検索パターンに末尾の空白をトリミングすることです。 回避策では、固定長データが最大有効桁数を持つ型し、パターンを検索する rtrim 関数を適用する値の式のキャストを作成します。  
  
-   ASE 動作の選択を使用する**使用**です。  
  
-   既定値を使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 動作**を使わない**です。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**使用しないでください  
  
**フル モード:**使用  
  
**REPLICATE 関数**  
REPLICATE 関数では、文字列の指定した回数だけ繰り返されます。 文字列、ゼロ回繰り返し、指定した場合は ASE で、結果が null です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure、結果は、空の文字列。  
  
-   ASE 動作を使用するには、次のように選択します。 **Replace 関数**です。 REPLICATE 関数に対するすべての呼び出しは、(で作成したスキーマ名 's2ss' でユーザー データベース) Sybase ASE 動作をエミュレートするために渡されるパラメーターの型に基づく REPLICATE_VARCHAR または REPLICATE_NVARCHAR のいずれかのユーザー定義関数の呼び出しに置き換えられます。  
  
-   既定値を使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure 動作**Replace 関数**です。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード/フル モード:** Replace 関数  
  
**TRIM (LTRIM、RTRIM) 関数**  
この設定では、Trim (LTRIM、RTRIM) 関数への呼び出し、Sybase ASE と同等の構文を関数で置き換えますか、現在の構文を保持するかどうかを指定します。 次のオプションは、この特定の設定。  
  
-   **Replace 関数**  
  
-   **現在の構文を保持します。**  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード/フル モード:** Replace 関数  
  
**SUBSTRING 関数**  
ASE、関数で`SUBSTRING(expression, start, length)`式の文字数より大きい開始値が指定されている場合、または長さが 0 に等しい場合は NULL を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/SQL Azure、同等の式が空の文字列を返します。  
  
-   ASE 動作を使用するには、次のように選択します。 **Replace 関数**です。 SUBSTRING 関数のすべての呼び出しは、(で作成したスキーマ名 's2ss' でユーザー データベース) Sybase ASE 動作をエミュレートするために渡されるパラメーターの型に基づく SUBSTRING_VARCHAR または SUBSTRING_NVARCHAR SUBSTRING_VARBINARY のユーザー定義関数の呼び出しに置き換えられます。  
  
-   使用する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] /SQL Azure 動作**現在の構文を保持**です。  
  
変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。  
  
**既定/Optimistic モード:**現在の構文を保持  
  
**フル モード:** Replace 関数  
  
## <a name="tables"></a>TABLES  
**Primary key を追加します。**  
新しい主キーを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Access のテーブルには、主キーまたは一意のインデックスがあるない場合は SQL Azure のテーブルです。  
  
-   **既定のモード**: False  
  
-   **オプティミスティック モード**: False  
  
-   **Full モード**: True  
  
> [!NOTE]  
> SQL Azure に接続しているときは、既定では True です。  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイス リファレンス & #40 です。SybaseToSQL &#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  

