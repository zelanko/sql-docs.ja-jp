---
title: "プロジェクトの設定 (変換) (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016 Preview
ms.assetid: a98a5e07-eb5e-47b9-a6f2-e2cb3a18309c
caps.latest.revision: "15"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 62451526ad29a0aaf2d2cc92e3e439223e6c32d3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="project-settings-conversion-oracletosql"></a>プロジェクトの設定 (変換) (OracleToSQL)
[変換] ページ、**プロジェクト設定** ダイアログ ボックスには、SSMA を Oracle の構文に変換する方法をカスタマイズする設定が含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文です。  
  
変換ウィンドウがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   すべての SSMA プロジェクトの設定を指定する、**ツール**ボタンをクリックし**プロジェクト設定の既定の**、設定は表示または変更に必要な移行プロジェクトの種類を選択**移行対象のバージョン**ドロップダウン、をクリックして**全般**クリックして、左側のウィンドウの下部にある**変換**です。  
  
-   現在のプロジェクトの設定を指定する、**ツール**ボタンをクリックし**プロジェクト設定**、順にクリックして**全般**クリックして、左側のウィンドウの下部にある**変換**です。  
  
## <a name="conversion-messages"></a>変換メッセージ  
  
|||  
|-|-|  
|項目|定義|  
|**問題の適用に関するメッセージを生成します。**|SSMA に変換中に情報メッセージを生成し、出力ウィンドウに表示され、変換後のコードに追加するかどうか指定します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック モード:**なし<br /><br />**フル モード:**なし|  
  
## <a name="miscellaneous-options"></a>その他のオプション  
  
|||  
|-|-|  
|項目|定義|  
|**整数値としてキャスト ROWNUM 式**|SSMA ROWNUM 式が変換されるときに、TOP 句は、後に、式に、式を変換します。 次の例では、Oracle 削除ステートメントで ROWNUM を示しています。<br /><br />`DELETE FROM Table1`<br /><br />`WHERE ROWNUM < expression and Field1 >= 2`<br /><br />次の例は、結果として得られる[!INCLUDE[tsql](../../includes/tsql_md.md)]:<br /><br />`DELETE TOP (expression-1)`<br /><br />`FROM Table1`<br /><br />`WHERE Field1>=2`<br /><br />一番上では、TOP 句の式が整数に評価されたことが必要です。 整数が負の場合、ステートメントはエラーを生成します。<br /><br />選択した場合**はい**SSMA は、整数として式をキャストします。<br /><br />選択した場合**いいえ**SSMA では、整数以外のすべての式は変換後のコードのエラーとしてマークします。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/フル モード:**なし<br /><br />**オプティミスティック モード:** [はい]|  
|**既定のスキーマのマッピング**|この設定は、SQL Server スキーマを Oracle スキーマをマップする方法を指定します。 2 つのオプションは、この設定で使用できます。<br /><br />**データベースにスキーマ:** Oracle このモードで 'sch1' のスキーマを既定では 'dbo' SQL Server データベースのスキーマを SQL Server 'sch1' にマップされます。<br /><br />**スキーマをスキーマ:**Oracle このモードで 'sch1' のスキーマを既定では、接続ダイアログで提供される既定の SQL Server データベース内の 'sch1' SQL Server スキーマにマップされます。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/Optimistic/フル モード:**データベースにスキーマ|  
|**MERGE ステートメントの変換方法**|選択した場合**を使用して INSERT、UPDATE、DELETE ステートメント**、SSMA 変換は、合併のステートメントが INSERT、UPDATE、DELETE ステートメント。<br /><br />選択した場合**MERGE を使用してステートメント**、SSMA 変換合併ステートメントに MERGE ステートメント[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br />**注:**このプロジェクトの設定オプションでのみ使用可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2008 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 です。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/Optimistic/フル モード:** MERGE を使用するステートメント|  
|**既定の引数を使用してサブプログラムへの呼び出しに変換します。**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]関数は、関数呼び出しでパラメーターの省略をサポートしていません。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]関数およびプロシージャ パラメーターの既定値として式をサポートしています。<br /><br />選択した場合**[はい]**関数呼び出しのパラメーターを省略して、SSMA は、キーワードを挿入する**既定**関数と、正しい場所に呼び出しにします。 次に、警告の呼び出しを設定します。<br /><br />選択した場合**いいえ**SSMA はエラーとして関数呼び出しとしてマークされます。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**COUNT 関数を COUNT_BIG に変換します。**|かどうか、カウントの関数は、2,147, 483,647 を超える値を返す可能性の高い 2<sup>31</sup>-1、COUNT_BIG を関数に変換する必要があります。<br /><br />選択した場合**はい**SSMA は COUNT_BIG を使用するすべての数を変換します。<br /><br />選択した場合**いいえ**関数にカウントとして残ります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]関数が 2 よりも大きい値を返す場合、エラーが返されます<sup>31</sup>-1 です。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/フル モード:** [はい]<br /><br />**オプティミスティック モード:**なし|  
|**FORALL ステートメント間に変換ステートメント**|SSMA PL/SQL コレクション要素に対して FORALL ループを処理できる方法を定義します。<br /><br />選択した場合**はい**SSMA をコレクションの要素が 1 つずつ取得が WHILE ループを作成します。<br /><br />選択した場合**いいえ**SSMA は、ノードに関するページ () メソッドを使用して、コレクションから行セットを生成し、1 つのテーブルとして使用します。 これによりより効率的ですが、出力コードが読みにくくなります。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック モード:**なし<br /><br />**フル モード:** [はい]|  
|**SET NULL 参照操作である列に指定された変換の外部キーが NOT NULL します。**|Oracle では外部キー制約を作成する場所を NULL に設定の操作可能性のあるを実行できませんでした参照先の列で null 値が許可されていないためです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]このような外部キーの構成は許可されません。<br /><br />選択した場合**はい**SSMA Oracle の場合と同様に参照動作が生成されますが、制約を読み込む前に手動で変更する必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 たとえば、SET NULL ではなく、NO ACTION を選択できます。<br /><br />選択した場合**いいえ**制約は、エラーとしてマークされます。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:**なし|  
|**プロシージャ呼び出しの関数呼び出しに変換します。**|Oracle の一部の関数が自律的なトランザクションとして定義されますまたは有効ではありませんステートメントを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 このような場合は、SSMA は、手順と、プロシージャのラッパーである関数を作成します。 変換後の関数は、実装するプロシージャを呼び出します。<br /><br />SSMA は、プロシージャの呼び出しにラッパー関数の呼び出しを変換できます。 これによりより読みやすいコードを作成され、パフォーマンスを向上させることができます。 ただし、コンテキストは常にできません。たとえば、プロシージャ呼び出しで、選択リスト内の関数呼び出しを置き換えることはできません。 SSMA では、一般的なケースを取り入れるためのいくつかのオプションがあります。<br /><br />選択した場合**常に**SSMA はプロシージャ呼び出しをラッパー関数の呼び出しを変換しようとしています。 現在のコンテキストでは、この変換はできません、エラー メッセージが生成されます。 これにより、関数呼び出しが残っていないで生成されたコード。<br /><br />選択した場合**可能であれば**SSMA は、関数に出力パラメーターがある場合にのみプロシージャの呼び出しに移動を使用します。 移動が可能でない場合は、パラメーターの出力属性が削除されます。 その他のすべてのケースでは、SSMA は、関数呼び出しを残します。<br /><br />選択した場合**Never**SSMA は関数呼び出しとしてすべての関数呼び出しのままにします。 このオプションを選択できない可能性があります許容可能なパフォーマンス上の理由のためです。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/Optimistic/フル モード:**可能な場合|  
|**LOCK ステートメントを変換します。**|SSMA は、テーブル ヒントに多くのロック TABLE ステートメントを変換できます。 SSMA は、パーティション、副区分が含まれているすべてのロック テーブル ステートメントを変換できません@dblinkNOWAIT 句、および変換エラー メッセージでは、このようなステートメントをマークします。<br /><br />選択した場合**はい**SSMA を使用して、サポートされているロック TABLE ステートメントをテーブル ヒントに変換されます。<br /><br />選択した場合**いいえ**SSMA は変換のエラー メッセージのすべてのロック テーブル ステートメントとしてマークされます。<br /><br />次の表は、SSMA が Oracle ロック モードに変換する方法を示しています。<br /><br />**Oracle のロック モード**<br /><br />行の共有<br /><br />排他行<br /><br />共有の更新プログラムの行の共有を =<br /><br />共有<br /><br />共有<br /><br />排他的<br /><br />**SQL Server のテーブル ヒント**<br /><br />ROWLOCK、HOLDLOCK<br /><br />ROWLOCK、XLOCK、HOLDLOCK<br /><br />ROWLOCK、HOLDLOCK<br /><br />TABLOCK、HOLDLOCK<br /><br />TABLOCK、XLOCK、HOLDLOCK<br /><br />TABLOCKX、HOLDLOCK<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**REF CURSOR 出力パラメーターに対して開く FOR ステートメントを変換します。**|Oracle では、サブプログラムの REF CURSOR 型のパラメーターを設定の結果を返す FOR OPEN ステートメントを使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、ストアド プロシージャが直接 SELECT ステートメントの結果を返します。<br /><br />SSMA は、SELECT ステートメントに多くのオープン FOR ステートメントを変換できます。<br /><br />選択した場合**はい**SSMA をクライアントに結果セットを返す SELECT ステートメントに FOR OPEN ステートメントを変換します。<br /><br />選択した場合**いいえ**、SSMA 変換後のコードでは、出力ウィンドウで、エラー メッセージが生成されます。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**離職の変数の一覧としてレコードに変換します。**|SSMA は、分離変数と特定の構造を持つ XML 変数に、Oracle のレコードを変換できます。<br /><br />選択した場合**はい**SSMA は、可能であれば、離職変数の一覧をレコードに変換します。<br /><br />選択した場合**いいえ**SSMA は、特定の構造を持つ XML 変数にレコードを変換します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**SUBSTR 関数呼び出し関数の呼び出しを部分文字列との変換します。**|SSMA は Oracle SUBSTR 関数呼び出しに変換できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **substring**関数呼び出しのパラメーターの数によっては、します。 SSMA は SUBSTR 関数の呼び出しを変換できない、またはパラメーターの数がサポートされていません、SSMA は、カスタムの SSMA 関数呼び出しに SUBSTR 関数呼び出しを変換します。<br /><br />選択した場合**はい**、SSMA に 3 つのパラメーターを使用する SUBSTR 関数呼び出しに変換されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **substring**です。 その他の SUBSTR 関数は、カスタムの SSMA 関数を呼び出すに変換されます。<br /><br />選択した場合**いいえ**SSMA は、カスタムの SSMA 関数呼び出しを SUBSTR 関数呼び出しに変換します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック モード:** [はい]<br /><br />**フル モード:**なし|  
|**サブタイプに変換します。**|SSMA は、2 つの方法で PL/SQL サブタイプに変換できます。<br /><br />選択した場合**はい**、SSMA が作成されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ユーザー定義サブタイプを入力し、このサブタイプの各変数を使用します。<br /><br />選択した場合**いいえ**SSMA は基になる型とサブタイプのすべてのソース宣言を置き換えるし、通常どおりの結果を変換します。 この場合、その他の種類は作成されませんで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:**なし|  
|**シノニムを変換します。**|次の Oracle オブジェクトに対してシノニムに移行できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:<br /><br />テーブルと、オブジェクト テーブル<br /><br />ビューとオブジェクトのビュー<br /><br />ストアド プロシージャおよび関数<br /><br />具体化されたビュー<br /><br />**次の類義語**Oracle オブジェクトは、オブジェクトへの直接参照で置き換えることができます。<br /><br />シーケンス<br /><br />パッケージ<br /><br />Java クラスのスキーマ オブジェクト<br /><br />ユーザー定義オブジェクトの種類<br /><br />その他のシノニムを移行することはできません。 SSMA は、シノニムとシノニムを使用するすべての参照のエラー メッセージが生成されます。<br /><br />選択した場合**はい**、SSMA は作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]類義語と前の一覧に従って直接オブジェクト参照。<br /><br />選択した場合**いいえ**SSMA は、ここに表示されているすべてのシノニムを直接オブジェクト参照が作成されます。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**TO_CHAR (日付、形式) に変換します。**|SSMA は、Oracle TO_CHAR(date, format) を sysdb データベースからのプロシージャに変換することができます。<br /><br />選択した場合**を使用して TO_CHAR_DATE 関数**、SSMA TO_CHAR_DATE 関数を使用してに英語の言語の変換に TO_CHAR (日付、形式) を変換します。<br /><br />選択した場合**を使用して TO_CHAR_DATE_LS 関数 (NLS 注意が必要)**、SSMA TO_CHAR_DATE_LS 関数を使用してセッションの言語の変換のために TO_CHAR (日付、形式) を変換します<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/Optimistic モード:** Using TO_CHAR_DATE 関数<br /><br />**フル モード:** Using TO_CHAR_DATE_LS 関数 (NLS 注意が必要)|  
|**トランザクション処理ステートメントを変換します。**|SSMA は、Oracle トランザクション処理ステートメントに変換できます。<br /><br />選択した場合**はい**、SSMA 変換 Oracle トランザクション処理ステートメントを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ステートメントです。<br /><br />選択した場合**いいえ**、SSMA ステートメントの変換エラーを処理するトランザクション マークを付けます。<br /><br />**注:** Oracle トランザクションが暗黙的に開きます。 この動作をエミュレートするために[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、する必要があります BEGIN TRANSACTION ステートメントを手動で追加のトランザクションを開始する場所です。 代わりに、セッションの先頭に SET IMPLICIT_TRANSACTIONS ON コマンドを実行できます。 SSMA は、自律的なトランザクションでのサブルーチンを変換するときに自動的に SET IMPLICIT_TRANSACTIONS ON を追加します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**ORDER BY 句での Oracle null 動作をエミュレートします。**|NULL 値が異なる方法で並べ替えられて[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]と Oracle:<br /><br />[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、NULL 値は、順序付きリストで、最小値。 昇順の一覧では、NULL 値を先頭に表示されます。<br /><br />Oracle では、NULL 値は、最高値順序付きリストです。 既定では、NULL 値は昇順注文リストの最後に表示されます。<br /><br />Oracle では最初の null 値と null 値の最後の句を使用すると、Oracle による null 値の順序を変更します。<br /><br />SSMA は、NULL 値を確認する Oracle ORDER BY の動作をエミュレートすることができます。 最初に順にその他の値によって、指定された順序とし、注文に NULL 値です。<br /><br />選択した場合**はい**、SSMA Oracle ORDER BY の動作をエミュレートする方法で Oracle ステートメントに変換されます。<br /><br />選択した場合**いいえ**SSMA は Oracle の規則を無視し、最初の null 値と null 値の最後の句を検出すると、エラー メッセージを生成します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック モード:**なし<br /><br />**フル モード:** [はい]|  
|**選択内の行カウント例外をエミュレートします。**|INTO 句を伴う SELECT ステートメントがすべての行を返さない場合は Oracle に NO_DATA_FOUND 例外を発生させます。 ステートメントには、次の 2 つ以上の行が返されます、TOO_MANY_ROWS 例外が発生します。 変換後のステートメント[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]行の数が 1 つと異なる場合は、任意の例外を発生しません。<br /><br />選択した場合**はい**SSMA は、各 SELECT ステートメントの後に sysdb プロシージャ db_error_exact_one_row_check への呼び出しを追加します。 この手順では、NO_DATA_FOUND と TOO_MANY_ROWS の例外をエミュレートします。 これは既定値であり、できるだけ近くに Oracle 動作を再現することができます。 常に選択する必要があります**はい**ソース コードにこれらのエラーを処理する例外ハンドラーがある場合。 ユーザー定義関数の内部で SELECT ステートメントが発生すると、このモジュールは、ストアド プロシージャを実行するためのストアド プロシージャに変換されますと、例外の発生と互換性がありません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]関数のコンテキスト。<br /><br />選択した場合**いいえ**例外は生成されません。 SSMA は、ユーザー定義関数を変換し、内の関数のままにする場合に利用をでき[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**DBMS_SQL のエラーを生成します。解析**|選択した場合**エラー**、SSMA DBMS_SQL 変換でエラーが生成されます。解析します。<br /><br />選択した場合**警告**、SSMA DBMS_SQL 変換で警告が生成されます。解析します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:**エラー|  
|**ROWID の列を生成します。**|SSMA を内のテーブルを作成すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ROWID 列を作成できます。 データを移行すると、各行は、newid() 関数によって生成される新しい UNIQUEIDENTIFIER 値を取得します。<br /><br />選択した場合**[はい]**、ROWID 列のすべてのテーブルの作成と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]値を挿入するように Guid を生成します。 常に選択する**はい**SSMA Tester を使用する予定の場合。<br /><br />選択した場合**いいえ**ROWID 列はテーブルに追加されません。<br /><br />**トリガーを持つテーブルに対して ROWID 列を追加する**トリガーを含むテーブルの ROWID を追加します。<br /><br />**注:** SQL Server 2005、SQL Server 2008 および SQL Server 2012 および 2014 の場合、既定の設定は**テーブルのトリガーを使用しての列を追加 ROWID**です。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/Optimistic モード:**トリガーを持つテーブルに対して ROWID 列を追加します。<br /><br />**フル モード:** [はい]|  
|**ROWID の列に一意のインデックスを生成します。**|SSMA に ROWID が生成される列に一意のインデックス列が生成されるかどうかどうかを指定します。 一意のインデックスが生成されたオプションが"YES"に設定されている場合と"NO"に設定されている場合、一意のインデックスは、ROWID 列は生成されません。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**ローカル モジュールの変換**|入れ子になった oracle サブプログラム (保管されたスタンドアロンのプロシージャまたは関数で宣言) 変換の種類を定義します。<br /><br />選択した場合**インライン**、入れ子になったサブプログラム呼び出しに置き換えられますの本文。<br /><br />選択した場合**ストアド プロシージャ**入れ子になったサブプログラムは、SQL Server のストアド プロシージャに変換されます、およびその呼び出しは、次のプロシージャ呼び出しに置き換えられます。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:**インライン|  
|**文字列の連結で ISNULL を使用します。**|Oracle および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]文字列連結で NULL 値を含める場合は、異なる結果を返します。 Oracle では、NULL 値は、空の文字セットと同様に扱われます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]NULL を返します。<br /><br />選択した場合**はい**、SSMA は、Oracle の連結文字 (&#124; &#124;) を置き換えますで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]連結文字 (+)。 SSMA では、NULL 値を連結したものの両方の側の式も確認します。<br /><br />選択した場合**いいえ**SSMA は連結文字を置き換えますが、NULL 値をチェックしません。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**置換関数の呼び出しに ISNULL を使用します。**|ISNULL ステートメントは、Oracle の動作をエミュレートするために置換関数の呼び出しに使用されます。 次のオプションは、この設定に存在します。<br /><br />YES<br /><br />いいえ<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック モード:**なし<br /><br />**フル モード:** [はい]|  
|**CONCAT 関数呼び出しに ISNULL を使用します。**|ISNULL ステートメントは、Oracle の動作をエミュレートする CONCAT 関数呼び出しに使用されます。 次のオプションは、この設定に存在します。<br /><br />YES<br /><br />いいえ<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック モード:**なし<br /><br />**フル モード:** [はい]|  
|**可能な場合は、ネイティブの convert 関数を使用します。**|選択した場合**はい**SSMA は、可能な場合は、ネイティブの convert 関数に TO_CHAR (日付、形式) を変換します。<br /><br />選択した場合**いいえ**、SSMA TO_CHAR_DATE または TO_CHAR_DATE_LS (これは、"変換 TO_CHAR(date, format)"オプションを使用して定義されます) に TO_CHAR (日付、形式) を変換します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック モード:** [はい]<br /><br />**フル モード:**なし|  
|**選択を使用してください.FOR XML 変換するときに次のように選択してください.レコードの変数の INTO**|レコードの変数を選択すると設定 XML 結果を生成するかどうかを指定します。<br /><br />選択した場合**はい**、SELECT ステートメントは、XML を返します。<br /><br />選択した場合**いいえ**、SELECT ステートメントが結果セットを返します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:**なし|  
  
## <a name="returning-clause-conversion"></a>句の変換を返す  
  
|||  
|-|-|  
|項目|定義|  
|**DELETE ステートメント内での RETURNING 句を出力に変換します。**|Oracle では、すぐに削除された値を取得する方法として、RETURNING 句を提供します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]OUTPUT 句と共に、その機能を提供します。<br /><br />選択した場合**はい**SSMA が DELETE ステートメント内の RETURNING 句を OUTPUT 句に変換されます。 テーブルのトリガーには、値を変更できる、ので、返される値が異なることがあります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Oracle の場合よりもします。<br /><br />選択した場合**いいえ**、SSMA 返される値を取得する DELETE ステートメントより前に、SELECT ステートメントが生成されます。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**INSERT ステートメントで RETURNING 句を出力に変換します。**|Oracle では、すぐに挿入する値を取得する方法として、RETURNING 句を提供します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]OUTPUT 句と共に、その機能を提供します。<br /><br />選択した場合**はい**SSMA は、INSERT ステートメントで RETURNING 句を出力に変換されます。 テーブルのトリガーには、値を変更できる、ので、返される値が異なることがあります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Oracle の場合よりもします。<br /><br />選択した場合**いいえ**SSMA では、Oracle の機能をエミュレートを挿入し、参照テーブルから値を選択します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
|**UPDATE ステートメントで RETURNING 句を出力に変換します。**|Oracle では、すぐに更新された値を取得する方法として、RETURNING 句を提供します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]OUTPUT 句と共に、その機能を提供します。<br /><br />選択した場合**はい**SSMA は UPDATE ステートメントで RETURNING 句を OUTPUT 句に変換されます。 テーブルのトリガーには、値を変更できる、ので、返される値が異なることがあります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Oracle の場合よりもします。<br /><br />選択した場合**いいえ**SSMA は返される値を取得する UPDATE ステートメントの後に SELECT ステートメントを生成します。<br /><br />変換モードを選択すると、**モード**SSMA ボックスには、次の設定が適用されます。<br /><br />**既定/オプティミスティック/全モード:** [はい]|  
  
## <a name="sequence-conversion"></a>シーケンスの変換  
  
|||  
|-|-|  
|項目|定義|  
|**シーケンス ジェネレーターを変換します。**|Oracle では、一意の識別子を生成するのにシーケンスを使用することができます。<br /><br />SSMA は、次に、シーケンスを変換できます。<br /><br />(このオプションはのみ使用可能な場合に SQL Server 2012 および SQL Server 2014 への変換) SQL Server シーケンス ジェネレーターを使用します。<br /><br />SSMA シーケンス ジェネレーターを使用します。<br /><br />列の id を使用します。<br /><br />SQL Server 2012 または SQL Server 2014 に変換する際の既定のオプションでは、SQL Server のシーケンス ジェネレーターを使用します。 ただし、SQL Server 2012 および SQL Server 2014 がサポートしていません (Oracle シーケンス currval メソッドなど) の現在のシーケンス値を取得します。 Oracle シーケンス currval メソッドを移行する方法については、SSMA チーム ブログ サイトを参照してください。<br /><br />SSMA では、SSMA シーケンス エミュレーターに Oracle シーケンスに変換するためのオプションも提供します。 これは、SQL Server 2012 より前変換する場合の既定のオプション<br /><br />最後に、SQL Server の id 値をテーブル内の列に割り当てられたシーケンスを変換することもできます。 Oracle で identity 列をシーケンスの間のマッピングを指定する必要があります**テーブル** タブ|  
|**トリガーの外部の CURRVAL を変換します。**|変換のシーケンス ジェネレーターに設定されている場合にのみ表示されます**列 id を使用して**です。 Oracle シーケンスはテーブルとは別のオブジェクトであるため、シーケンスを使用して多数のテーブルを生成し、新しいシーケンス値の挿入トリガーを使用します。 SSMA は、これらのステートメントをコメントまたはコメント アウトがエラーを生成するときにエラーとしてマークを付けます。<br /><br />選択した場合**はい**SSMA は、変換後のトリガーの外部には、警告と共に CURRVAL をシーケンス処理を行うすべての参照としてマークされます。<br /><br />選択した場合**いいえ**SSMA は、変換後のトリガーの外部には、エラーで CURRVAL をシーケンス処理を行うすべての参照としてマークされます。|  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイス リファレンス &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
