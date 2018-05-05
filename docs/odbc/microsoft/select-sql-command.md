---
title: SQL コマンドの選択 - |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- select [ODBC]
ms.assetid: 2149c3ca-3a71-446d-8d53-3d056e2f301a
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d3803c1e51a21e8006994db5ba89f9b2cb41ad6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="select---sql-command"></a>SQL コマンドを選択します。
1 つまたは複数のテーブルからデータを取得します。  
  
 Visual FoxPro ODBC ドライバーでは、このコマンドのネイティブの Visual FoxPro 言語の構文をサポートしています。 ドライバー固有の情報を参照してください。**ドライバー解説**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [ALL | DISTINCT]  
   [Alias.] Select_Item [AS Column_Name]  
   [, [Alias.] Select_Item [AS Column_Name] ...]   
FROM [DatabaseName!]Table [Local_Alias]  
   [, [DatabaseName!]Table [Local_Alias] ...]   
[WHERE JoinCondition [AND JoinCondition  
…]  
   [AND | OR FilterCondition [AND | OR FilterCondition ...]]]  
[GROUP BY GroupColumn [, GroupColumn ...]]  
[HAVING FilterCondition]  
[UNION [ALL] SELECTCommand]  
[ORDER BY Order_Item [ASC | DESC] [, Order_Item [ASC | DESC] ...]]  
```  
  
## <a name="arguments"></a>引数  
  
> [!NOTE]  
>  A*サブクエリ*、次の引数で参照される、SELECT 内の SELECT は、かっこで囲む必要があります。 同じレベルに最大 2 つのサブクエリを持つことができます (入れ子になっていない) WHERE 句でします。 (引数の特定のセクションを参照してください)。サブクエリでは、複数の結合条件を含めることができます。  
  
 [すべて&#124;DISTINCT]  [*エイリアス*]。*Select_Item* [AS *Column_Name*] [、[*エイリアス*]。*Select_Item* [AS *Column_Name*]...]  
 SELECT 句では、フィールド、定数、およびクエリの結果に表示される式を指定します。  
  
 既定は、クエリ結果内のすべての行すべて表示します。  
  
 DISTINCT では、クエリの結果からすべての行の重複部分を除外します。  
  
> [!NOTE]  
>  DISTINCT を 1 回だけを使用するには SELECT 句で指定します。  
  
 *エイリアス*です。 一致する項目の名前を修飾します。 各項目で指定した*Select_Item*クエリ結果の 1 つの列が生成されます。 2 つまたは複数の項目が同じ名前である場合は、テーブルの別名と列が重複することを防止する項目の名前の前にピリオドが含まれます。  
  
 *Select_Item*クエリの結果に含まれる項目を指定します。 項目には、次のいずれかを指定できます。  
  
-   FROM 句でテーブルからのフィールドの名前。  
  
-   同じ定数値がクエリの結果のすべての行に表示されることを指定する定数。  
  
-   ユーザー定義関数の名前を指定できる式です。  
  
 **選択をユーザー定義関数**  
  
 SELECT 句でユーザー定義関数を使用して明らかな利点がありますが、次の制限事項も検討する必要があります。  
  
-   選択を実行する操作の速度は、このようなユーザー定義関数を実行する速度によって制限があります。 ユーザー定義関数を含む大規模な操作は、API と C# またはアセンブリ言語で記述されたユーザー定義関数を使用してより実現可能性があります。  
  
-   選択から呼び出されるユーザー定義関数に値を渡す唯一信頼できる方法が呼び出されると、関数に渡される引数リストです。  
  
-   実験して FoxPro の特定のバージョンで正常に動作すると思われる禁止された操作を検出した場合でも、引き続きそれ以降のバージョンで動作する保証はありません。  
  
 これらの制限とは別のユーザー定義関数は、SELECT 句で可能です。 ただし、SELECT を使用すると、パフォーマンスが低下することに注意してください。  
  
 次のフィールドの関数は、フィールドまたはフィールドを含む式は、選択項目で使用可能です。  
  
-   AVG (*Select_Item*)、数値データの列の平均を計算します。  
  
-   カウント (*Select_Item*)-列の選択項目の数をカウントします。 COUNT(*) は、クエリ出力に行の数をカウントします。  
  
-   MIN (*Select_Item*) — の最小値を決定*Select_Item*列にします。  
  
-   MAX (*Select_Item*) — の最大値を決定*Select_Item*列にします。  
  
-   SUM (*Select_Item*)、数値データの列を合計します。  
  
 フィールド関数を入れ子にすることはできません。  
  
 AS *Column_Name*  
 クエリ出力に列の見出しを指定します。 これによりときに*Select_Item*式は、またはフィールドを含む関数し、列にわかりやすい名前を付けることです。 *Column_Name*式を指定できますが、テーブルのフィールド名は許可されない文字 (スペースなど) を含めることはできません。  
  
 [*DatabaseName*!]*テーブル*[*Local_Alias*] [、[*DatabaseName*!]*テーブル*[*Local_Alias*]...]  
 クエリによって取得されるデータを含むテーブルを一覧表示します。 開いているテーブルがない場合は、Visual FoxPro が表示されます、**開く** ダイアログ ボックスのファイルの場所を指定できるようにします。 これが開かれた後、クエリが完了した後の表は開いています。  
  
 *DatabaseName*! データ ソースに指定されている以外のデータベースの名前を指定します。 データ ソースと、データベースが指定されていない場合は、テーブルを含むデータベースの名前を含める必要があります。 データベース名の後に感嘆符 (!) 区切り記号は、テーブル名の前にあります。  
  
 *Local_Alias*で指定したテーブルの一時的な名前を指定*テーブル*です。 ローカルのエイリアスを指定する場合は、SELECT ステートメントでテーブル名の代わりにローカルのエイリアスを使用する必要があります。 ローカルのエイリアスでは、Visual FoxPro 環境は影響しません。  
  
 ここで*JoinCondition* [AND *JoinCondition* ...]   [AND&#124;または*FilterCondition* [AND&#124;または*FilterCondition* ...]  
 Visual FoxPro、クエリの結果に特定のレコードだけを含めるように指示します。 複数のテーブルからデータを取得するために必要な場所です。  
  
 *JoinCondition* FROM 句でテーブルをリンクするフィールドを指定します。 クエリで複数のテーブルを含める場合、最初より後のすべてのテーブルの結合条件を指定する必要があります。  
  
> [!IMPORTANT]  
>  結合条件を作成するときに、次の情報を考慮してください。  
  
-   クエリに 2 つのテーブルを含めるし、結合条件を指定しない場合、フィルター条件が満たされている限り、最初のテーブルのすべてのレコードが 2 番目のテーブルのすべてのレコードに参加しています。 このようなクエリでは、長い結果を生成できます。  
  
-   Visual FoxPro が空のフィールドと一致するために、空のフィールドを持つテーブルを結合する際に、注意を使用します。 たとえば、顧客に参加する場合です。Zip 圧縮し、請求します。Zip 圧縮し、クエリ出力に空のフィールドを結果として得られる 40,000 の余分なレコードが含まれています顧客には、空の 100 の zip コードが含まれています、請求書には、空の zip コードが 400 が含まれている場合は、します。 使用して、**空 ()** 関数をクエリ出力から空のレコードを削除します。  
  
-   AND 演算子を使用して、複数の結合条件を接続する必要があります。 各 join 条件には、次の形式があります。  
  
     *FieldName1 比較 FieldName2*  
  
     *FieldName1* 1 つのテーブルからのフィールドの名前を指定*FieldName2*別のテーブルのフィールドの名前を指定および*比較*は次の表で説明されている演算子の 1 つです。  
  
|演算子|比較|  
|--------------|----------------|  
|=|等号|  
|==|正確に等しい|  
|LIKE|SQL のような|  
|<>, !=, #|等しくないです。|  
|>|以上|  
|>=|大きいか等しい|  
|<|より小さい|  
|<=|以下|  
  
 使用すると、= 演算子、文字列、その機能は、異なる設定の ANSI の設定に応じて。 ANSI の設定が OFF に設定されている場合、Visual FoxPro は Xbase ユーザーになじみ方法で文字列比較を処理します。 ANSI の設定が ON に設定されている場合、Visual FoxPro には、文字列比較のための ANSI 規格に従います。 参照してください[設定の ANSI](../../odbc/microsoft/set-ansi-command.md)と[設定の正確な](../../odbc/microsoft/set-exact-command.md)Visual FoxPro が文字列比較を実行する方法の詳細についてはします。  
  
 *FilterCondition*クエリの結果に含まれるレコードが満たす必要がある条件を指定します。 AND で接続すること、必要な数のフィルター クエリ内の条件を含めることができますか、OR 演算子。 NOT 演算子を使用して、論理式の値を反転するまたは使用することができます**空 ()** 空のフィールドを確認します。 *FilterCondition*次の例で、フォームのいずれかを実行できます。  
  
 **例 1** *FieldName1 比較 FieldName2*  
  
 `customer.cust_id = orders.cust_id`  
  
 **例 2** *FieldName 比較式*  
  
 `payments.amount >= 1000`  
  
 **例 3** *FieldName 比較*すべて (*サブクエリ*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 フィルター条件には、すべてが含まれている場合、フィールドは、そのレコードは、クエリの結果に追加する前に、サブクエリによって生成されたすべての値の比較条件を満たす必要があります。  
  
 **例 4** *FieldName 比較*ANY &#124; SOME (*サブクエリ*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 フィルター条件は、いずれかまたはいくつか含まれている場合、フィールドは、サブクエリによって生成された値の少なくとも 1 つの比較条件を満たす必要があります。  
  
 次の例は、フィールドの値が値の指定した範囲内かどうかを確認します。  
  
 **例 5** *FieldName* [NOT] BETWEEN *Start_Range* AND *End_Range*  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 次の例は、少なくとも 1 つの行が、サブクエリの条件を満たすかどうかを確認します。 フィルター条件が True に評価されたフィルター条件には、EXISTS が含まれている場合 (です。T.) は空のセットにサブクエリが評価される場合を除き、します。  
  
 **例 6** [NOT] が存在する (*サブクエリ*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **例 7** *FieldName* [NOT] IN *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 フィルター条件に含まれる場合、そのレコードは、クエリの結果に追加する前に、フィールドが、値のいずれかを含める必要があります。  
  
 **例 8** *FieldName* [NOT] IN (*サブクエリ*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 ここで、フィールドは、そのレコードは、クエリの結果に追加する前に、サブクエリによって返される値のいずれかに含める必要があります。  
  
 **例 9** *FieldName* [NOT] LIKE *cExpression*  
  
 `customer.country NOT LIKE "USA"`  
  
 このフィルター条件に一致する各フィールドを検索*cExpression*です。 一部として、パーセント記号 (%) とアンダー スコア (_) ワイルドカード文字を使用することができます*cExpression*です。 アンダー スコアでは、文字列内の 1 つの不明な文字を表します。  
  
 GROUP BY *GroupColumn* [、 *GroupColumn* ...]  
 1 つまたは複数の列の値に基づいて、クエリ内の行をグループ。 *GroupColumn*次のいずれかになります。  
  
-   通常のテーブルのフィールドの名前。  
  
-   SQL フィールド関数を含むフィールドです。  
  
-   結果のテーブル内の列の位置を示す数値式です。 (左端の列数は 1 です)。  
  
 持つ*FilterCondition*  
 クエリの結果に含まれるグループが満たす必要があるフィルター条件を指定します。 HAVING は GROUP BY を使用する必要があり、AND で接続されている、必要な数のフィルター条件に含めることができますか、OR 演算子。 また、論理式の値を逆に使用することができます。  
  
 *FilterCondition*サブクエリを含めることはできません。  
  
 GROUP BY 句を使用せず、HAVING 句は、WHERE 句と同様に動作します。 HAVING 句では、ローカルのエイリアスとフィールド関数を使用できます。 HAVING 句にフィールド関数が含まれていない場合は、パフォーマンスを向上させる、WHERE 句を使用します。  
  
 [ALL] 共用体*SELECTCommand*]  
 別の選択の最終的な結果を 1 つの SELECT の最終結果を結合します。 既定は、共用体は、結合された結果を確認し、重複する行を排除します。 かっこを使用して、複数の UNION 句を結合します。  
  
 すべては共用体が結合された結果から重複する行を排除することを防止します。  
  
 UNION 句では、これらの規則に従います。  
  
-   共用体を使用して、サブクエリを結合することはできません。  
  
-   両方のコマンドを選択、クエリ出力に同じ数の列が必要です。  
  
-   1 つの SELECT のクエリ結果内の各列は、その他の選択に対応する列として、同じデータ型と幅が必要です。  
  
-   最後の選択だけ、ORDER BY 句を番号で出力列を参照する必要があることができます。 ORDER BY 句が含まれる場合は、完全な結果に影響します。  
  
 外部結合をシミュレートするために UNION 句を使用することもできます。  
  
 クエリで 2 つのテーブルを結合すると、出力では、結合フィールドに値が一致するレコードのみが含まれています。 親テーブル内のレコードには、子テーブル内の対応するレコードがない場合、親テーブル内のレコードは出力には含まれません。 外部結合では、出力では、子テーブル内の一致レコードと親テーブルのすべてのレコードを挿入することができます。 Visual FoxPro で外部結合を作成するには、次の例のように、入れ子になった SELECT コマンドを使用する必要があります。  
  
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
>  含まれる各セミコロンの直前にあるスペースを含めることを確認します。 それ以外の場合、エラーが表示されます。  
  
 UNION 句では、両方のテーブルからレコードを選択する前に、コマンドのセクションがある一致する値。 関連する請求書がない顧客の会社は含まれません。 UNION 句の後にコマンドのセクションでは、一致するレコードを orders テーブルではありません顧客テーブルにレコードを選択します。  
  
 コマンドの 2 番目のセクションについては、次を注意してください。  
  
-   かっこで囲まれた SELECT ステートメントは、最初に処理されます。 このステートメントは、orders テーブルのすべての顧客数の選択範囲を作成します。  
  
-   WHERE 句は、orders テーブルに含まれていない、customer テーブル内のすべてのカスタマー番号を検索します。 コマンドの最初のセクションでは、orders テーブルの顧客番号のあるすべての会社が提供される、ために、customer テーブルのすべての企業は、クエリの結果に含めるようになりました。  
  
-   2 番目の SELECT ステートメントを表す 2 つのプレース ホルダーは、共用体に含まれるテーブルの構造は同じでなければならないので*orders.order_id*と*orders.emp_id*最初の SELECT からステートメント。  
  
    > [!NOTE]  
    >  プレース ホルダーは、それらを表すフィールドと同じ型である必要があります。 プレース ホルダーをする必要があります、フィールドが日付型の場合は、{//}。 フィールドが文字のフィールドの場合は、プレース ホルダーは、空の文字列をする必要があります ("") です。  
  
 ORDER BY *Order_Item* [ASC &#124; DESC] [、 *Order_Item* [ASC &#124; DESC]...]  
 1 つまたは複数の列のデータをに基づいて、クエリの結果を並べ替える。 各*Order_Item*クエリ結果内の列に対応して、次のいずれかになります。  
  
-   テーブルのフィールドに、FROM (サブクエリ) ではなくメイン SELECT 句で select 項目になっています。  
  
-   結果のテーブル内の列の位置を示す数値式です。 (左端の列の番号は 1 です)。  
  
 ASC は、注文項目または項目、に従って、クエリの結果を昇順を指定します、ORDER BY の既定値です。  
  
 DESC では、クエリ結果を降順の順序を指定します。  
  
 ORDER BY で注文を指定しない場合は、順序付けられていないクエリの結果が表示されます。  
  
## <a name="remarks"></a>解説  
 選択は、その他の Visual FoxPro コマンドと同様に、Visual FoxPro に組み込まれている SQL コマンドです。 使用すると、クエリが発生する場合に選択、Visual FoxPro、クエリを解釈し、指定されたデータをテーブルから取得します。 コマンド プロンプト ウィンドウまたは Visual FoxPro プログラムのいずれかの中から選択クエリを作成するには (と同様に、他の Visual FoxPro コマンド)。  
  
> [!NOTE]  
>  選択は、フィルターの設定で指定された現在のフィルター条件を反映されません。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 送信する場合、アプリケーション、ODBC SQL ステートメントを選択して、データ ソースに、Visual FoxPro ODBC ドライバーはコマンドには、ODBC エスケープ シーケンスが含まれていない場合、翻訳しないで Visual FoxPro SELECT コマンドにコマンドを変換します。 ODBC エスケープ シーケンスで囲まれた項目は、Visual FoxPro 構文に変換されます。 詳細については、ODBC を使用してエスケープ シーケンスは、「[時刻および日付関数](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md)し、、 *Microsoft ODBC プログラマ リファレンス*、を参照してください[odbc エスケープ シーケンス](../../odbc/reference/develop-app/escape-sequences-in-odbc.md).  
  
## <a name="see-also"></a>参照  
 [SQL テーブルを作成します。](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL](../../odbc/microsoft/insert-sql-command.md)   
 [セットの ANSI](../../odbc/microsoft/set-ansi-command.md)   
 [正確な設定します。](../../odbc/microsoft/set-exact-command.md)
