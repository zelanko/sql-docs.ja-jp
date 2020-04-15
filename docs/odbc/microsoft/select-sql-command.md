---
title: 選択 - SQL コマンド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- select [ODBC]
ms.assetid: 2149c3ca-3a71-446d-8d53-3d056e2f301a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 640189a5a31d0c21642b037e906bd6361690a9a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300942"
---
# <a name="select---sql-command"></a>SELECT - SQL コマンド
1 つ以上のテーブルからデータを取得します。  
  
 ビジュアル フォックスプロ ODBC ドライバーは、このコマンドのネイティブの Visual FoxPro 言語構文をサポートしています。 ドライバ固有の情報については、「**ドライバ解説**」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [ALL | DISTINCT]  
   [Alias.] Select_Item [AS Column_Name]  
   [, [Alias.] Select_Item [AS Column_Name] ...]   
FROM [DatabaseName!]Table [Local_Alias]  
   [, [DatabaseName!]Table [Local_Alias] ...]   
[WHERE JoinCondition [AND JoinCondition  
...]  
   [AND | OR FilterCondition [AND | OR FilterCondition ...]]]  
[GROUP BY GroupColumn [, GroupColumn ...]]  
[HAVING FilterCondition]  
[UNION [ALL] SELECTCommand]  
[ORDER BY Order_Item [ASC | DESC] [, Order_Item [ASC | DESC] ...]]  
```  
  
## <a name="arguments"></a>引数  
  
> [!NOTE]  
>  次の引数で参照される*サブクエリ*は SELECT 内で、かっこで囲む必要があります。 WHERE 句には、同じレベル (入れ子になっていない) に最大 2 つのサブクエリを含めることができます。 (引数のそのセクションを参照してください。サブクエリには複数の結合条件を含めることができます。  
  
 [すべての&#124;異なる]  [*エイリアス*.]*Select_Item* [AS *Column_Name]**[,*[ エイリアス .]*Select_Item* *[AS Column_Name]*..  
 SELECT 句は、クエリ結果に表示されるフィールド、定数、および式を指定します。  
  
 既定では、ALL はクエリ結果のすべての行を表示します。  
  
 DISTINCT は、クエリ結果からすべての行の重複を除外します。  
  
> [!NOTE]  
>  DISTINCT は、SELECT 句ごとに 1 回だけ使用できます。  
  
 *エイリアス*: 一致する項目名を修飾します。 Select_Item*で指定*した各項目は、クエリ結果の 1 つの列を生成します。 複数の項目が同じ名前の場合は、列が重複しないように、テーブルの別名と項目名の前にピリオドを含めます。  
  
 *Select_Item*クエリ結果に含める項目を指定します。 アイテムは、次のいずれかになります。  
  
-   FROM 句のテーブルのフィールドの名前。  
  
-   同じ定数値がクエリ結果のすべての行に表示されることを指定する定数。  
  
-   ユーザー定義関数の名前を指定できる式。  
  
 **SELECT を使用したユーザー定義関数**  
  
 SELECT 句でユーザー定義関数を使用すると、明らかな利点がありますが、次の制限も考慮する必要があります。  
  
-   SELECT を使用して実行される操作の速度は、そのようなユーザー定義関数が実行される速度によって制限される場合があります。 ユーザー定義関数を含む大量操作は、C 言語またはアセンブリ言語で記述された API およびユーザー定義関数を使用することで、より適切に実行できます。  
  
-   SELECT から呼び出されるユーザー定義関数に値を渡す唯一の信頼できる方法は、関数が呼び出されたときに関数に渡される引数リストです。  
  
-   特定のバージョンの FoxPro で正しく動作すると思われる操作を実験して発見しても、それ以降のバージョンで動作し続ける保証はありません。  
  
 これらの制限とは別に、ユーザー定義関数は SELECT 句で使用できます。 ただし、SELECT を使用するとパフォーマンスが低下する可能性があることに注意してください。  
  
 フィールドまたはフィールドを含む式である選択項目では、次のフィールド関数を使用できます。  
  
-   *AVG(Select_Item)-* 数値データの列を平均します。  
  
-   COUNT(*Select_Item*) - 列内の選択項目の数をカウントします。 COUNT(*) は、クエリ出力の行数をカウントします。  
  
-   MIN(*Select_Item*) - 列の*Select_Item*の最小値を決定します。  
  
-   MAX(*Select_Item*) - 列の*最大値Select_Item*を決定します。  
  
-   SUM(*Select_Item*) - 数値データの列を合計します。  
  
 フィールド関数を入れ子にすることはできません。  
  
 as *Column_Name*  
 クエリ出力の列の見出しを指定します。 これは、*式Select_Item、* またはフィールド関数を含み、列にわかりやすい名前を付ける場合に便利です。 *Column_Name*式は可能ですが、テーブルフィールド名に使用できない文字 (例えば、スペース) を含めることはできません。  
  
 [*データベース名*!]*テーブル*[*Local_Alias*]*[, [データベース名*!]*テーブル*[*Local_Alias*] ..  
 クエリが取得するデータを含むテーブルを一覧表示します。 テーブルが開かなければ、[**開く**] ダイアログ ボックスが表示され、ファイルの場所を指定できます。 開いた後、テーブルはクエリが完了した後も開いたままになります。  
  
 *データベース名*! データ ソースで指定されたデータベース以外のデータベースの名前を指定します。 データ ソースでデータベースが指定されていない場合は、テーブルを含むデータベースの名前を含める必要があります。 データベース名の後、テーブル名の前に感嘆符 (!) 区切り記号を含めます。  
  
 *Local_Alias*は Table*で指定*したテーブルの一時名を指定します。 ローカル別名を指定する場合は、SELECT ステートメント全体でテーブル名の代わりにローカル別名を使用する必要があります。 ローカル エイリアスは、ビジュアル FoxPro 環境には影響しません。  
  
 どこで*ジョインコンディション*[アンド*ジョインコンディション*.]   [および&#124;または*フィルター条件*[および&#124;または*フィルター条件*..]  
 クエリ結果に特定のレコードのみを含むように Visual FoxPro に指示します。 複数のテーブルからデータを取得するには、WHERE が必要です。  
  
 *JoinCondition は*、FROM 句内のテーブルをリンクするフィールドを指定します。 クエリに複数のテーブルを含める場合は、最初のテーブルの後に各テーブルに結合条件を指定する必要があります。  
  
> [!IMPORTANT]  
>  結合条件を作成する場合は、次の情報を考慮してください。  
  
-   クエリに 2 つのテーブルを含め、結合条件を指定しない場合、フィルタ条件が満たされている限り、最初のテーブルのすべてのレコードが 2 番目のテーブルのすべてのレコードに結合されます。 このようなクエリでは、長い結果が生成される可能性があります。  
  
-   空のフィールドと一致する Visual FoxPro のテーブルを結合する場合は注意してください。 たとえば、CUSTOMER に参加する場合などです。ZIPと請求書。ZIP と CUSTOMER に 100 個の空の郵便番号が含まれ、INVOICE に 400 個の空の郵便番号が含まれている場合、クエリの出力には、空のフィールドから得られる 40,000 個の追加レコードが含まれます。 **EMPTY( )** 関数を使用して、クエリ出力から空のレコードを除去します。  
  
-   複数の結合条件を接続するには、AND 演算子を使用する必要があります。 各結合条件の形式は次のとおりです。  
  
     *フィールド名1 比較フィールド名2*  
  
     *FieldName1*は 1 つのテーブルのフィールドの名前 *、FieldName2*は別のテーブルのフィールドの名前、*比較*は次の表で説明する演算子の 1 つです。  
  
|演算子|比較|  
|--------------|----------------|  
|=|Equal|  
|==|まさに等しい|  
|LIKE|SQL のような|  
|<>、!=、#|等しくない|  
|>|以上|  
|>=|以上または等しい|  
|<|より小さい|  
|<=|以下|  
  
 文字列で = 演算子を使用すると、SET ANSI の設定によって動作が異なります。 SET ANSI が OFF に設定されている場合、Visual FoxPro は Xbase ユーザーになじみのある方法で文字列比較を処理します。 SET ANSI を ON に設定すると、文字列比較に関する ANSI 標準に従います。 Visual FoxPro が文字列比較を実行する方法の詳細については[、「ANSI](../../odbc/microsoft/set-ansi-command.md)の設定」および[「正確な設定](../../odbc/microsoft/set-exact-command.md)」を参照してください。  
  
 *FilterCondition は*、クエリ結果に含めるには、レコードが満たす必要がある条件を指定します。 クエリに必要な数だけフィルタ条件を含めることができ、AND または OR 演算子で接続できます。 また、NOT 演算子を使用して論理式の値を逆にしたり **、EMPTY( ) を**使用して空のフィールドをチェックすることもできます。 *FilterCondition*は、次の例の任意のフォームを取ることができます。  
  
 **例 1** *フィールド名 1 の比較フィールド名2*  
  
 `customer.cust_id = orders.cust_id`  
  
 **例 2** *フィールド名の比較式*  
  
 `payments.amount >= 1000`  
  
 **例 3** *フィールド名の比較*ALL (*サブクエリ*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 フィルター条件に ALL が含まれる場合、フィールドは、サブクエリによって生成されたすべての値の比較条件を満たし、そのレコードがクエリ結果に含まれる必要があります。  
  
 **例 4** *フィールド名の比較*ANY &#124; SOME (*サブクエリ*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 フィルタ条件に ANY または SOME が含まれる場合、フィールドは、サブクエリによって生成された値のうち少なくとも 1 つの比較条件を満たす必要があります。  
  
 次の例では、フィールドの値が指定された範囲内にあるかどうかを確認します。  
  
 **例 5***フィールド名*[NOT] *Start_Range*と*End_Range*の間  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 次の例では、少なくとも 1 つの行がサブクエリの条件を満たしているかどうかを確認します。 フィルター条件に EXISTS が含まれる場合、フィルター条件は True (.T.) サブクエリが空のセットに評価されない限り。  
  
 **例 6** [NOT] EXISTS (*サブクエリ*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **例 7** *フィールド名*[NOT] in *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 フィルタ条件に IN が含まれる場合、フィールドに値の 1 つが含まれている必要があります。  
  
 **例 8** *フィールド名*[NOT] IN (*サブクエリ*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 このフィールドには、サブクエリが返す値の 1 つが含まれている必要があります。  
  
 **例 9** *フィールド名*[NOT] LIKE *c 式*  
  
 `customer.country NOT LIKE "USA"`  
  
 このフィルタ条件は *、cExpression*に一致する各フィールドを検索します。 パーセント記号 (%)およびアンダースコア ( _ ) ワイルドカード文字を cExpression の一部として*使用します*。 アンダースコアは、文字列内の 1 つの不明な文字を表します。  
  
 *グループ列別グループ列* *[, グループ列*.]  
 1 つ以上の列の値に基づいて、クエリの行をグループ化します。 *グループ列*は、次のいずれかになります。  
  
-   通常のテーブル フィールドの名前。  
  
-   SQL フィールド関数を含むフィールド。  
  
-   結果表内の列の位置を示す数値式。 (左端の列番号は 1 です。  
  
 *フィルタ条件を*持つ  
 クエリ結果に含めるグループが満たす必要があるフィルター条件を指定します。 HAVING は GROUP BY と共に使用し、AND または OR 演算子で接続されたフィルター条件を必要なだけ含めることができます。 また、NOT を使用して論理式の値を逆にすることもできます。  
  
 *フィルタ条件に*サブクエリを含めることはできません。  
  
 GROUP BY 句を含まない HAVING 句は、WHERE 句のように動作します。 HAVING 句では、ローカル エイリアスとフィールド関数を使用できます。 HAVING 句にフィールド関数が含まれている場合は、パフォーマンスを向上するために WHERE 句を使用します。  
  
 [ユニオン [すべて]*コマンドを選択]*  
 ある SELECT の最終結果と、別の SELECT の最終結果を結合します。 既定では、UNION は結合された結果をチェックし、重複する行を削除します。 複数の UNION 句を結合するには、かっこを使用します。  
  
 ALL は、UNION が結合された結果から重複する行を除去することを防ぎます。  
  
 UNION 句は、次の規則に従います。  
  
-   UNION を使用してサブクエリを結合することはできません。  
  
-   どちらの SELECT コマンドも、クエリ出力に同じ数の列を含める必要があります。  
  
-   1 つの SELECT のクエリ結果の各列は、他の SELECT の対応する列と同じデータ型と幅を持つ必要があります。  
  
-   最終的な SELECT だけが ORDER BY 句を持つことができます。 ORDER BY 句が含まれている場合、完全な結果に影響します。  
  
 UNION 句を使用して外部結合をシミュレートすることもできます。  
  
 クエリ内の 2 つのテーブルを結合すると、結合フィールドの値が一致するレコードのみが出力に含まれます。 親テーブルのレコードに子テーブルに対応するレコードがない場合、親テーブルのレコードは出力に含まれません。 外部結合を使用すると、親テーブルのすべてのレコードを、子テーブル内の一致するレコードと共に出力に含めることができます。 Visual FoxPro で外部結合を作成するには、次の例のように、入れ子になった SELECT コマンドを使用する必要があります。  
  
```  
SELECT customer.company, orders.order_id, orders.emp_id ;  
FROM customer, orders ;  
WHERE customer.cust_id = orders.cust_id ;  
UNION ;  
SELECT customer.company, 0, 0 ;  
FROM customer ;  
WHERE customer.cust_id NOT IN ;  
(SELECT orders.cust_id FROM orders)  
```  
  
> [!NOTE]  
>  各セミコロンの直前のスペースを含めます。 それ以外の場合は、エラーが表示されます。  
  
 UNION 句の前のコマンドのセクションでは、値が一致する両方のテーブルからレコードが選択されます。 関連付けられた請求書がない顧客会社は含まれません。 UNION 句の後のコマンドのセクションでは、注文テーブルに一致するレコードがない顧客テーブルのレコードが選択されます。  
  
 コマンドの 2 番目のセクションに関しては、次の点に注意してください。  
  
-   括弧内の SELECT ステートメントが最初に処理されます。 この明細書では、受注テーブル内のすべての顧客番号の選択を作成します。  
  
-   WHERE 句は、受注テーブルにない顧客テーブル内のすべての顧客番号を検索します。 コマンドの最初のセクションでは、注文テーブルに顧客番号を持つすべての会社が提供されるため、顧客テーブルのすべての会社がクエリ結果に含まれるようになりました。  
  
-   UNION に含まれるテーブルの構造は同じである必要があるため、2 番目の SELECT ステートメントには、最初の SELECT ステートメントから*orders.order_id*と*orders.emp_id*を表す 2 つのプレースホルダーがあります。  
  
    > [!NOTE]  
    >  プレースホルダは、そのプレースホルダが表すフィールドと同じ型である必要があります。 フィールドが日付型の場合、プレースホルダは { / / } にする必要があります。 フィールドが文字フィールドの場合、プレースホルダーは空の文字列 ("") にする必要があります。  
  
 Order_Item[ASC &#124; DESC] *[Order_Item* [ASC &#124; DESC..] *Order_Item*  
 1 つ以上の列のデータに基づいて、クエリ結果を並べ替えます。 各*Order_Item*は、クエリ結果の列に対応する必要があり、次のいずれかになります。  
  
-   メイン SELECT 句の選択項目でもある FROM テーブルのフィールド (サブクエリ内ではありません)。  
  
-   結果表内の列の位置を示す数値式。 (左端の列は 1 番です。  
  
 ASC は、注文項目に従ってクエリ結果の昇順を指定し、ORDER BY のデフォルトです。  
  
 DESC は、クエリ結果の降順を指定します。  
  
 ORDER BY で注文を指定しない場合、クエリ結果は順序付けされずに表示されます。  
  
## <a name="remarks"></a>解説  
 SELECT は、他のビジュアル フォックス プロ コマンドと同様に、ビジュアル フォックス プロに組み込まれている SQL コマンドです。 SELECT を使用してクエリを実行すると、Visual FoxPro はクエリを解釈し、テーブルから指定されたデータを取得します。 コマンド プロンプト ウィンドウまたは Visual FoxPro プログラム (他の Visual FoxPro コマンドと同様) から SELECT クエリを作成できます。  
  
> [!NOTE]  
>  SELECT は、SET FILTER で指定された現在のフィルター条件を考慮しません。  
  
## <a name="driver-remarks"></a>ドライバの解説  
 アプリケーションが ODBC SQL ステートメント SELECT をデータ ソースに送信すると、コマンドに ODBC エスケープ シーケンスが含まれている場合を除き、Visual FoxPro ODBC ドライバーは、変換なしでコマンドを Visual FoxPro SELECT コマンドに変換します。 ODBC エスケープ シーケンスに含まれる項目は、Visual FoxPro 構文に変換されます。 ODBC エスケープ シーケンスの使用の詳細については、「[時刻関数と日付関数](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md)」および *「ODBC プログラマ リファレンス*」を参照してください。 [Escape Sequences in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md)  
  
## <a name="see-also"></a>参照  
 [テーブルの作成 - SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [挿入 - SQL](../../odbc/microsoft/insert-sql-command.md)   
 [ANSI を設定する](../../odbc/microsoft/set-ansi-command.md)   
 [正確な設定](../../odbc/microsoft/set-exact-command.md)
