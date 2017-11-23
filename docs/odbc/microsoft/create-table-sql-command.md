---
title: "テーブルの SQL コマンドを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CREATE TABLE [ODBC]
ms.assetid: be2143ba-fc16-42c9-84f7-8985cd924860
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6c8c6d75686741d1835f46a5ad7a64ab04c6925f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="create-table---sql-command"></a>テーブルの SQL コマンドを作成します。
指定されたフィールドを持つテーブルを作成します。  
  
 Visual FoxPro ODBC ドライバーでは、このコマンドのネイティブの Visual FoxPro 言語の構文をサポートしています。 ドライバー固有の情報を参照してください。**ドライバー解説**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE TABLE | DBF TableName1 [NAME LongTableName] [FREE]  
   (FieldName1FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]   
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
   [, FieldName2 ...]  
      [, PRIMARY KEY eExpression2 TAG TagName2  
      |, UNIQUE eExpression3 TAG TagName3]  
      [, FOREIGN KEY eExpression4 TAG TagName4 [NODUP]  
            REFERENCES TableName3 [TAG TagName5]]  
      [, CHECK lExpression2 [ERROR cMessageText2]])  
| FROM ARRAY ArrayName  
```  
  
## <a name="arguments"></a>引数  
 テーブル &#124; を作成します。DBF *TableName1*  
 作成するテーブルの名前を指定します。 テーブルと DBF のオプションは同じです。  
  
 名前*LongTableName*  
 テーブルの長い名前を指定します。 長いテーブル名がデータベースに格納されているために、データベースが開いたときにのみ、長いテーブル名を指定することができます。  
  
 長い名前は最大 128 文字を含めることができ、データベース内の短いファイル名の代わりに使用できます。  
  
 FREE  
 テーブルを開いているデータベースに追加されませんされますを指定します。 データベースが開いていない場合、空きは必要ありません。  
  
 *(FieldName1 FieldType* [( *nFieldWidth* [、 *nPrecision*])]  
 フィールド名、フィールドの型、フィールドの幅、およびフィールドの有効桁数 (小数点以下桁数の番号) をそれぞれ指定します。  
  
 *FieldType*を示す、フィールドの 1 つの文字は、[データ型](../../odbc/microsoft/visual-foxpro-field-data-types.md)です。 一部のフィールドのデータ型を指定することを必要と*nFieldWidth*または*nPrecision*またはその両方です。  
  
 *nFieldWidth*と*nPrecision* D、G、I、L、M、P、T、および Y を無視する型。 *nPrecision*の既定値は 0 (小数点以下の桁数) 場合*nPrecision* B、F、または N 型に含まれていません。  
  
 NULL  
 フィールドの null 値を許可します。  
  
 NOT NULL  
 フィールドの null 値を防ぎます。  
  
 NULL を省略して NOT NULL、SET NULL の現在の設定は、フィールドで null 値を許容するかどうかを決定します。 ただし、NOT NULL NULL を省略し、主キーまたは一意の句を含む、NULL に設定の現在の設定は無視され、フィールドの既定値は NOT NULL します。  
  
 確認*lExpression1*  
 フィールドの検証規則を指定します。 *lExpression1*ユーザー定義関数であることができます。 空のレコードを追加するたびに検証規則がチェックされます。 検証規則が追加されたレコード内の空白のフィールド値を許可しない場合は、エラーが生成されます。  
  
 エラー *cMessageText1*  
 Visual FoxPro 表示フィールド規則は、エラーを生成するときにエラー メッセージを指定します。 [参照] ウィンドウまたは編集ウィンドウ内でデータが変更された場合にのみ、メッセージが表示されます。  
  
 既定の*eExpression1*  
 フィールドの既定値を指定します。 データ型*eExpression1*フィールドのデータ型と同じである必要があります。  
  
 PRIMARY KEY  
 フィールドのプライマリ インデックスを作成します。 プライマリ インデックス タグは、フィールドと同じ名前を持ちます。  
  
 UNIQUE  
 フィールドの候補のインデックスを作成します。 候補インデックス タグは、フィールドと同じ名前を持ちます。  
  
> [!NOTE]  
>  候補 (CREATE TABLE または ALTER TABLE - SQL に固有のオプションを含めることによって作成される) インデックスは、一意インデックス コマンド オプションで作成されたインデックスと同じではありません。 INDEX コマンドの一意のオプションを使用して作成されたインデックスにより、重複したインデックスのキーです。候補となるインデックスでは、重複するインデックス キーは許可されません。 参照してください[インデックス](../../odbc/microsoft/index-command.md)その固有のオプションの詳細についてはします。  
  
 Null 値と重複するレコードは、プライマリまたは候補のインデックスのためのフィールドには使用できません。 ただし、null 値をサポートするフィールドのプライマリまたは候補のインデックスを作成する場合、Visual FoxPro はエラーを生成しません。 Visual FoxPro には、プライマリまたは候補のインデックスのためのフィールドに null または重複した値を入力しようとする場合に、エラーが発生します。  
  
 参照*TableName2*[タグ*TagName1*]  
 永続的なリレーションシップが確立されている、親テーブルを指定します。 タグを省略した場合*TagName1*、親テーブルのプライマリ インデックスのキーを使用して、関係を確立します。 親テーブルがプライマリ インデックスを持たない場合、Visual FoxPro はエラーを生成します。  
  
 タグを含める*TagName1*親テーブルの既存のインデックス タグに基づく関係を確立します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。  
  
 親テーブルには、無料のテーブルをすることはできません。  
  
 NOCPTRANS  
 文字とメモ フィールドを異なるコード ページに変換しないようにします。 テーブルは別のコード ページに変換する場合、NOCPTRANS が指定されているフィールドは変換されません。 NOCPTRANS は、文字とメモ フィールドに対してのみ指定できます。  
  
 次の例では、2 つの文字フィールドとメモ型の 2 つのフィールドを含む mytable という名前のテーブルを作成します。 2 番目の文字のフィールド、char2、および 2 番目のメモ フィールド memo2、翻訳を防ぐために NOCPTRANS が含まれます。  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 主キー *eExpression2*タグ*TagName2*  
 プライマリ インデックスを作成するを指定します。 *eExpression2*テーブルのすべてのフィールドまたはフィールドの組み合わせを指定します。 タグ*TagName2 の*作成されるプライマリ インデックス タグの名前を指定します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。  
  
 テーブルに 1 つだけのプライマリ インデックスはため、フィールドのプライマリ インデックスを既に作成している場合にこの句を含めることはできません。 Visual FoxPro では、テーブルの作成に主キーの 1 つ以上の句を含める場合は、エラーが生成されます。  
  
 一意な*eExpression3*タグ*TagName3*  
 候補のインデックスを作成します。 *eExpression3*テーブルのすべてのフィールドまたはフィールドの組み合わせを指定します。 ただし、プライマリ キーのオプションのいずれかのプライマリ インデックスを作成した場合は、プライマリ インデックスの指定されたフィールドを含めることはできません。 タグ*TagName3 の*を作成する候補インデックス タグのタグ名を指定します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。  
  
 テーブルには、複数の候補となるインデックスを持つことができます。  
  
 外部キー *eExpression4*タグ*TagName4*[NODUP]  
 外部 (非) インデックスを作成し、親テーブルとのリレーションシップを確立します。 *eExpression4*外部インデックスのキー式を指定し、 *TagName4*が作成される、外部インデックス キー タグの名前を指定*です。* タグ名のインデックスは、最大 10 個の文字を含めることができます。 候補外部インデックスを作成する NODUP が含まれます。  
  
 テーブルの複数の外部のインデックスを作成することができますが、外部インデックス式がテーブル内の別のフィールドを指定する必要があります。  
  
 参照*TableName3*[タグ*TagName5*]  
 永続的なリレーションシップが確立されている、親テーブルを指定します。 タグを含める*TagName5*親テーブルのインデックス タグに基づく関係を確立します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。 既定では、タグを省略した場合*TagName5、*親テーブルのプライマリ インデックスのキーを使用して、関係を確立します。  
  
 確認*eExpression2*[エラー *cMessageText2*]  
 テーブルの検証ルールを指定します。 エラー *cMessageText2* Visual FoxPro は、テーブルの検証ルールが実行されたときに表示されます。 エラー メッセージを指定します。 データが [参照] ウィンドウで変更されたか、編集ウィンドウ場合にのみ、メッセージが表示されます。  
  
 配列から*ArrayName*  
 名前、型、有効桁数、およびテーブル内の各フィールドの小数点以下桁数で構成される既存の配列の名前を指定します。 配列の内容を定義することができます、 **AFIELDS**() 関数です。  
  
## <a name="remarks"></a>解説  
 新しいテーブルが使用可能な作業を最小領域で開かれ、そのエイリアスでアクセスできます。 排他的な設定の現在の設定に関係なく、新しいテーブルが排他的に開かれます。  
  
 データベースが開かれていると、無料の句を含まない、新しいテーブルがデータベースに追加されます。 データベース内のテーブルと同じ名前で新しいテーブルを作成できません。  
  
 データベースが開いている場合、CREATE TABLE - SQL には、データベースを排他的に使用が必要です。 排他的に使用するためのデータベースを開くには、開くデータベースに排他的を含めます。  
  
 新しいテーブルを作成するときに、データベースが開かれていない、名前、CHECK、DEFAULT、外部キー、主キー、または参照の句を含むでエラーが発生します。  
  
> [!NOTE]  
>  CREATE TABLE 構文は、特定のテーブルの作成オプションを区切るコンマを使用します。 また、列の定義を含むかっこで囲まれた、NULL、いない NULL、チェック、既定値、主キー、および一意の句を配置しなければなりません。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 アプリケーションが ODBC SQL ステートメントを送信するとき Visual FoxPro ODBC ドライバーは、データ ソースにテーブルを作成、次の表に示す構文を使用して、ビジュアルの FoxProCREATE テーブル コマンド、コマンドに変換します。  
  
|ODBC 構文|Visual FoxPro 構文|  
|-----------------|--------------------------|  
|CREATE TABLE*ベース テーブル名*<br /><br /> (*列識別子のデータ型*<br /><br /> [NULL 以外]<br /><br /> [、*列識別子のデータ型*<br /><br /> [NOT NULL]...)|テーブルを作成する*TableName1* [名前*LongTableName*]<br /><br /> (*FieldName1* *FieldType*<br /><br /> [(*nFieldWidth* [、 *nPrecision*])]<br /><br /> [NULL 以外])|  
  
 ドライバーを使用してテーブルを作成するときに、ドライバーは、他のユーザーがテーブルにアクセスできるように作成後すぐに、テーブルを閉じます。 これは、テーブルが作成時のみに開いたままになる Visual FoxPro とは異なります。 ただし、CREATE TABLE ステートメントを含む、データ ソース上のストアド プロシージャを実行した場合、テーブルが開いたままにします。  
  
 Visual FoxPro ODBC ドライバーがという名前のテーブルを作成、データ ソースがデータベース (.dbc ファイル) の場合は、 *LongTableName*と同じ名前で、*ベース テーブル名*です。  
  
### <a name="using-data-definition-language-ddl"></a>データ定義言語 (DDL) を使用します。  
 DDL は、次の場所に含めることはできません。  
  
-   バッチの SQL ステートメントを必要とするトランザクション  
  
-   アプリケーションが最初に呼び出す場合を除き、トランザクションを必要とするステートメントの後に、手動コミット モードで**SQLTransact**です。  
  
 たとえば、一時テーブルを作成する場合は、トランザクションを必要とするステートメントを開始する前に、テーブルを作成する必要があります。 バッチ トランザクションを要求する SQL ステートメントに CREATE TABLE ステートメントを含めると、ドライバーは、エラー メッセージを返します。  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE の SQL コマンド](../../odbc/microsoft/alter-table-sql-command.md)   
 [サポートされるデータ型 (Visual FoxPro ODBC ドライバー)](../../odbc/microsoft/supported-data-types-visual-foxpro-odbc-driver.md)   
 [SQL コマンドを挿入します。](../../odbc/microsoft/insert-sql-command.md)   
 [SELECT - SQL コマンド](../../odbc/microsoft/select-sql-command.md)
