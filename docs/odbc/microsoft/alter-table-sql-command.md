---
title: ALTER TABLE の SQL コマンド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- alter table [ODBC]
ms.assetid: 3a01a291-f4d9-43bc-a725-5a95546ff364
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78f02df29883d59a2bed936ee1b5412c8dd6f178
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="alter-table---sql-command"></a>ALTER TABLE の SQL コマンド
プログラムによって、テーブルの構造を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER TABLE TableName1  
   ADD | ALTER [COLUMN] FieldName1  
      FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]  
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
 - Or -  
ALTER TABLE TableName1  
   ALTER [COLUMN] FieldName2  
      [NULL | NOT NULL]  
      [SET DEFAULT eExpression2]  
      [SET CHECK lExpression2 [ERROR cMessageText2]]  
      [DROP DEFAULT]  
      [DROP CHECK]  
 - Or -  
ALTER TABLE TableName1  
   [DROP [COLUMN] FieldName3]  
   [SET CHECK lExpression3 [ERROR cMessageText3]]  
   [DROP CHECK]  
   [ADD PRIMARY KEY eExpression3 TAG TagName2]  
   [DROP PRIMARY KEY]  
   [ADD UNIQUE eExpression4 [TAG TagName3]]  
   [DROP UNIQUE TAG TagName4]  
   [ADD FOREIGN KEY [eExpression5] TAG TagName4  
      REFERENCES TableName2 [TAG TagName5]]  
   [DROP FOREIGN KEY TAG TagName6 [SAVE]]  
   [RENAME COLUMN FieldName4 TO FieldName5]  
   [NOVALIDATE]  
```  
  
## <a name="arguments"></a>引数  
 *TableName1*  
 その構造が変更されたテーブルの名前を指定します。  
  
 [列] の追加*FieldName1*  
 追加するフィールドの名前を指定します。  
  
 ALTER [COLUMN] *FieldName1*  
 変更する既存のフィールドの名前を指定します。  
  
 *FieldType* [( *nFieldWidth* [、 *nPrecision*])  
 新しいまたは変更されたフィールドのフィールドの型、フィールドの幅、およびフィールドの有効桁数 (小数点以下桁数) を指定します。  
  
 *FieldType*を示す、フィールドの 1 つの文字は、[データ型](../../odbc/microsoft/visual-foxpro-field-data-types.md)です。 一部のフィールドのデータ型を指定することを必要と*nFieldWidth*または*nPrecision*またはその両方です。  
  
 *nFieldWidth*と*nPrecision* D、G、I、L、M、P、T、および Y を無視する型。 既定では、 *nPrecision*場合は 0 (数値) は、 *nPrecision*は、B、F、または N 型に含まれません。  
  
 NULL &#124; NOT NULL  
 許可または、フィールドの値は null を防止します。  
  
 NULL を省略して NOT NULL、SET NULL の現在の設定は、フィールドで null 値を許容するかどうかを決定します。 ただし、NOT NULL しし、主キーまたは一意の句を含める省略 NULL、SET NULL の現在の設定は無視されフィールドではありません既定では NULL です。  
  
 確認*lExpression1*  
 フィールドの検証規則を指定します。 *lExpression1*論理式を評価して、ユーザー定義関数またはストアド プロシージャを指定できます。 空のレコードを追加するたびに検証規則がチェックされます。 検証規則が追加されたレコード内の空白のフィールド値を許可しない場合は、エラーが生成されます。  
  
 エラー *cMessageText1*  
 フィールドの検証規則がエラーを生成するときに、エラー メッセージが表示されますを指定します。  
  
 既定の*eExpression1*  
 フィールドの既定値を指定します。 データ型*eExpression1*フィールドのデータ型と同じである必要があります。  
  
 PRIMARY KEY  
 プライマリ インデックスのタグを作成します。 インデックス タグは、フィールドと同じ名前を持ちます。  
  
 UNIQUE  
 フィールドと同じ名前を候補インデックス タグを作成します。  
  
> [!NOTE]  
>  候補 INDEX コマンドで、一意のオプションを使用して作成されたインデックスの違い (ALTER TABLE または CREATE TABLE で ANSI 互換性を保つのため、[一意] オプションを含めることによって作成される) のインデックス。 UNIQUE を INDEX コマンドを使用して作成されたインデックスにより、重複したインデックスのキーです。候補となるインデックスでは、重複するインデックス キーは許可されません。  
  
 Null 値と重複するレコードは、プライマリまたは候補のインデックスに使用されるフィールドには使用できません。  
  
 追加の列を使用して、新しいフィールドを作成する場合 Visual FoxPro はエラーを生成しません null 値をサポートするフィールドのプライマリまたは候補のインデックスを作成する場合。 ただし、Visual FoxPro であっても、プライマリまたは候補のインデックスに使用されるフィールドに null または重複した値を入力しようとする場合、エラーが生成されます。  
  
 既存のフィールドとなり、プライマリを変更するか、Visual FoxPro 候補インデックスの式は、テーブル内のフィールドで構成され、null 値または重複するレコードが含まれるかどうかを表示するフィールドを確認場合します。 場合は、Visual FoxPro、エラーが発生し、テーブルは変更されません。  
  
 参照*TableName2*タグ*TagName1*  
 永続的なリレーションシップが確立されている、親テーブルを指定します。 タグ*TagName1*リレーションシップの基になる、親テーブルのインデックスのタグを指定します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。  
  
 NOCPTRANS  
 文字とメモ フィールドを異なるコード ページに変換しないようにします。 テーブルは別のコード ページに変換する場合、NOCPTRANS が指定されているフィールドは変換されません。 NOCPTRANS は、文字とメモ フィールドに対してのみ指定できます。  
  
 次の例では、2 つの文字フィールドとメモ型の 2 つのフィールドを含む mytable という名前のテーブルを作成します。 2 番目の文字のフィールド、char2、および 2 番目のメモ フィールド memo2、翻訳を防ぐために NOCPTRANS が含まれます。  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 ALTER [COLUMN] *FieldName2*  
 変更する既存のフィールドの名前を指定します。  
  
 既定値に設定*eExpression2*  
 既存のフィールドの新しい既定値を指定します。 データ型*eExpression2*フィールドのデータ型と同じである必要があります。  
  
 セット チェック*lExpression2*  
 既存のフィールドに対して新しい検証規則を指定します。 *lExpression2*論理式を評価して、ユーザー定義関数またはストアド プロシージャがあります。  
  
 エラー *cMessageText2*  
 フィールドの検証規則がエラーを生成するときに、エラー メッセージが表示されますを指定します。 参照 または 編集ウィンドウ内でデータが変更された場合にのみ、メッセージが表示されます。  
  
 DROP DEFAULT  
 既存のフィールドの既定値を削除します。  
  
 ドロップ チェック  
 既存のフィールドの検証規則を削除します。  
  
 [列] ドロップ*FieldName3*  
 テーブルから削除するためのフィールドを指定します。 テーブルからフィールドを削除すると、フィールドの既定値の設定とフィールドの入力規則も削除します。  
  
 インデックスのキーまたはトリガーの式は、フィールドを参照する場合、式のフィールドが削除されたときに無効になりました。 この場合、フィールドが削除されますが、無効なインデックスのキーまたはトリガーの式は実行時にエラーを生成、エラーは生成されません。  
  
 セット チェック*lExpression3*  
 テーブルの検証ルールを指定します。 *lExpression3*論理式を評価して、ユーザー定義関数またはストアド プロシージャがあります。  
  
 エラー *cMessageText3*  
 テーブルの検証規則がエラーを生成するときに、エラー メッセージが表示されますを指定します。 参照 または 編集ウィンドウ内でデータが変更された場合にのみ、メッセージが表示されます。  
  
 ドロップ チェック  
 テーブルの検証規則を削除します。  
  
 追加のプライマリ キー *eExpression3*タグ*TagName2*  
 テーブルに、プライマリ インデックスを追加します。 *eExpression3*プライマリ インデックスのキー式を指定し、 *TagName2*プライマリ インデックス タグの名前を指定します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。 場合タグ*TagName2*が省略されていると*eExpression3* 1 つのフィールドは、プライマリ インデックス タグで指定されたフィールドとして同じ名前を持つ*eExpression3*です。  
  
 プライマリ キーを削除します  
 プライマリ インデックスとそのインデックスのタグを削除します。 テーブルが 1 つだけの主キーを持てないために、主キーの名前を指定する必要はありません。 プライマリ インデックスを削除すると、主キーに基づくすべての永続的なリレーションも削除されます。  
  
 追加 UNIQUE *eExpression4*[タグ*TagName3*]  
 候補のインデックスをテーブルに追加します。 *eExpression4*候補インデックスのキー式を指定し、 *TagName3*候補インデックス タグの名前を指定します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。 タグを省略した場合*TagName3*場合*eExpression4* 1 つのフィールドは、候補インデックス タグで指定されたフィールドとして同じ名前を持つ*eExpression4*です。  
  
 一意のタグをドロップ*TagName4*  
 候補のインデックスとそのインデックスのタグを削除します。 テーブルには、複数の候補キーを持つことができます、ために、候補インデックス タグの名前を指定する必要があります。  
  
 外部キーの追加 [ *eExpression5*] タグ*TagName4*  
 テーブルに外部の (非) インデックスを追加します。 *eExpression5*外部インデックスのキー式を指定し、 *TagName4*外部インデックス タグの名前を指定します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。  
  
 参照*TableName2*[タグ*TagName5*]  
 永続的なリレーションシップが確立されている、親テーブルを指定します。 タグを含める*TagName5*親テーブルの既存のインデックス タグに基づく関係を確立します。 タグ名のインデックスは、最大 10 個の文字を含めることができます。 タグを省略した場合*TagName5*、親テーブルのプライマリ インデックスのタグを使用して、関係を確立します。  
  
 ドロップの外部キー タグ*TagName6*[保存]  
 インデックスのタグは、外部キーを削除*TagName6*です。 保存を省略すると、インデックスのタグは構造のインデックスから削除されます。 構造のインデックスからインデックス タグの削除を防ぐために保存する が含まれます。  
  
 名前を変更する列*FieldName4*TO *FieldName5*  
 テーブル内のフィールドの名前を変更できます。 *FieldName4*名前を変更するフィールドの名前を指定します。 *FieldName5*フィールドの新しい名前を指定します。  
  
> [!CAUTION]  
>  インデックス式、フィールドとテーブルの検証規則、コマンド、および関数は、元のフィールド名を参照場合がありますのでテーブルのフィールドの名前を変更する場合は注意してください。  
  
 NOVALIDATE  
 Visual FoxPro テーブルの構造体への変更が使用できることを指定します。これらの変更は、テーブル内のデータの整合性を侵害する可能性があります。 既定では、Visual FoxPro より、テーブル内のデータの整合性に違反する変更が ALTER TABLE を防止します。 この既定の動作をオーバーライドする NOVALIDATE が含まれます。  
  
## <a name="remarks"></a>解説  
 データベースに追加されていない、テーブルの構造を変更するのには、ALTER TABLE を使用できます。 ただし、Visual FoxPro は、既定、外部キー、主キー、参照、またはフリー テーブルを変更する場合は、句を設定する場合、エラーを生成します。  
  
 ALTER TABLE では、新しいテーブルのヘッダーを作成し、テーブル ヘッダーにレコードを追加することによって、テーブルを再構築可能性があります。 たとえば、フィールドの型または幅を変更するには、テーブルを再構築する可能性があります。  
  
 テーブルが再構築後は、種類または幅が変更されているフィールドのフィールド検証ルールが実行されます。 型またはテーブルの任意のフィールドの幅を変更すると、テーブルのルールが実行されます。  
  
 レコードのあるテーブルのフィールドまたはテーブルの検証規則を変更する場合、Visual FoxPro は既存のデータに対して新しいフィールドまたはテーブルの検証ルールをテストしで最初に見つかった位置のフィールドまたはテーブルの検証規則またはトリガーに違反の警告を発行します。  
  
 変更するテーブルがデータベースでは、ALTER TABLE の場合、SQL には、データベースを排他的に使用が必要です。 排他的に使用するためのデータベースを開くには、開くデータベースに排他的を含めます。  
  
## <a name="see-also"></a>参照  
 [テーブルの SQL コマンドを作成します。](../../odbc/microsoft/create-table-sql-command.md)   
 [INDEX コマンド](../../odbc/microsoft/index-command.md)
