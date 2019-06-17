---
title: 静的データ マスク | Microsoft Docs
ms.date: 04/10/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: a62f4ff9-2953-42ca-b7d8-1f8f527c4d66
author: aliceku
ms.author: aliceku
manager: ajayj
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1cf3b95ec5836ac86770bd0cd9784f0617b91846
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65580979"
---
# <a name="static-data-masking"></a>静的データ マスク
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

静的データ マスキングは、[SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) 18.0 プレビュー 5 以降のコンポーネントとしてリリースされました。 
> [!IMPORTANT]
> Microsoft では、現在のプロトタイプはお客様の期待を満たしていないと判断しました。 そのため、この機能の今後の改良は行われない予定です。 これに代わるものが用意できた場合、弊社の計画を改めてお知らせします。
>



![静的データ マスク](../../relational-databases/security/media/sql-static-data-masking/static_data_masking_intro_image.PNG)


## <a name="what-is-static-data-masking"></a>静的データ マスクとは 
静的データ マスクは SQL Server Management Studio の機能であり、データベースのマスクされたコピーを作成することができます。 機密性の高いものが含まれるデータを、チーム間または他組織との間で共有する必要がある組織のために開発された機能です。 

静的データ マスクとで機密データ (マスク前のデータ) を新しいデータ (マスク後のデータ) に置き換えることで、次のシナリオが容易になります。 
- 開発とテスト 
- 分析とビジネス レポート 
- トラブルシューティング 
- コンサルタント、調査チーム、またはサード パーティとのデータベースの共有 

次の例では、静的データ マスクの動作方法のしくみを示します。 マスクが行われる前、列には社会保障番号が含まれています。 マスクが行われた後は、各社会保障番号の最初の 5 桁が、ランダムに生成された番号によって置き換えられています。

| 米国の社会保障番号 (マスク前)   | 米国の社会保障番号 (マスク後)  |
| ------------- | ------------- |
| 140-38-9110 | 302-92-9110 |
| 463-34-5535 | 189-70-5535 |
| 116-30-8733 | 201-01-8733 |
| 209-36-1971 | 683-10-1971 |
| 372-38-6948 | 372-38-6948 |
| 267-64-2334 | 100-03-2334 |
| 523-93-4176 | 582-20-4176 |
| 573-91-5137 | 730-20-5137 |
| 612-72-1026 | 369-40-1026 |

静的データ マスクのユーザーは、複数のマスク機能から選択できます。 マスク機能次第で、マスク前のデータとマスク後のデータの関連が、高くなることも、まったくなくなることもあります。 シャッフルを実行するマスク機能では、マスク前データとマスク後データの関連性が高くなります。 

| 米国の社会保障番号 (マスク前) | 米国の社会保障番号 (マスク後) |
| ------------- | ------------- |
| 140-38-9110 | 612-72-1026 |  
| 463-34-5535 | 372-38-6948 | 
| 116-30-8733 | 523-93-4176 |
| 209-36-1971 | 209-36-1971 | 
| 372-38-6948 | 140-38-9110 |
| 267-64-2334 | 463-34-5535 | 
| 523-93-4176 | 573-91-5137 | 
| 573-91-5137 | 267-64-2334 | 
| 612-72-1026 | 116-30-8733 |

NULL 値での置換を実行するマスク機能では、マスク前データとマスク後データの関連性がなくなります。 
 
| 米国の社会保障番号 (マスク前) | 米国の社会保障番号 (マスク後) |
| ------------- | ------------- |
| 140-38-9110 | NULL |  
| 463-34-5535 | NULL | 
| 116-30-8733 | NULL |
| 209-36-1971 | NULL | 
| 372-38-6948 | NULL |
| 267-64-2334 | NULL | 
| 523-93-4176 | NULL | 
| 573-91-5137 | NULL | 
| 612-72-1026 | NULL |

## <a name="how-does-static-data-masking-work"></a>静的なデータ マスクの動作
静的データ マスクは列レベルで行われます。 ユーザーは、マスクする列と、各列に適用するマスク機能を選択します。 複数のマスク機能から選択できます。 詳しくは、「[マスク機能](#masking-functions)」で説明します。 

静的データ マスクでは、データベースのコピーが作成されます。 Azure SQL Database の場合、コピーは[コピー機能](https://azure.microsoft.com/blog/static-data-masking-preview/)によって実行されます。 SQL Server の場合は、バックアップ操作とその後の復元操作によって実行されます。 その後、各列のマスク前のデータが、選択したマスク機能に従って、マスク後のデータに置き換えられます。 

置換はストレージ レベルで行われます。 そのため、静的データ マスクの完了後に、データベースのマスクされたコピーからマスク前のデータを取得することはできません。

## <a name="how-to-guide"></a>攻略ガイド

静的データ マスクを実行する詳細な手順を次に示します。 
 
1. SQL Server Management Studio を起動します。 データベースに接続します。 左側の **[オブジェクト エクスプローラー]** ウィンドウで、[データベース] フォルダーを展開します。 マスクを行うデータベースを右クリックします。 **[タスク]** をクリックします。 **[データベースをマスク...(プレビュー)]** をクリックします。
 
 ![[タスク] メニュー](../../relational-databases/security/media/sql-static-data-masking/task_data_masking.PNG)
 
2. マスク構成ウィンドウが表示されます。 データベース内のすべてのテーブルが表示されます。 テーブルはスキーマごとにまとめられ、スキーマ内はアルファベット順になっています。 
 
 ![ユーザー インターフェイス](../../relational-databases/security/media/sql-static-data-masking/ui_dropdown.PNG)
 
3. テーブル名の近くのドロップダウン アイコンをクリックして、テーブル内のすべての列の一覧を表示します。 テーブル内の各列について、データ型と、列が null 許容かどうかが示されています。 Null 許容の列は、エントリとして NULL 値を受け取ることができる列です。 
 
 ![テーブルのドロップダウン](../../relational-databases/security/media/sql-static-data-masking/ui_dropdown_column.png)
 
4. マスクするすべての列と、適用するマスク機能を選択します。 使用可能なマスクの種類は、 **[Shuffle]\(シャッフル\)** マスク、 **[Group Shuffle]\(グループ シャッフル\)** マスク、 **[Single Value]\(単一値\)** マスク、 **[NULL]** マスク、 **[String Composite]\(文字列合成\)** マスクです。 
 
 ![マスク機能ドロップダウン](../../relational-databases/security/media/sql-static-data-masking/masking_functions.PNG)
 
 注:これらのマスク機能のほとんどには、追加の構成パラメーターがあります。 シャッフル マスクについては、既定のパラメーターが提供されています。 グループ シャッフル マスク、単一値マスク、文字列合成マスクについては、ユーザーが構成パラメーターを指定する必要があります。 構成パラメーターを変更または指定するには、 **[構成...]** オプションをクリックし、ポップアップ表示されるダイアログ ボックスでパラメーターの (代替) 値を指定します。 各マスク機能について詳しくは、「[マスク機能](#masking-functions)」をご覧ください。
 
 ![マスク機能の構成ボタン](../../relational-databases/security/media/sql-static-data-masking/masking_functions_configure.png)
 
 マスク構成の指定は、その場で、構成関連およびスキーマ関連のエラーと警告を検証されます。  検出されたものは左側にアイコンとして示され、それをマウスでポイントすると、追加情報が表示されます。 
 
 次の例では、ユーザーは、NULL 値が許容されていない (NOT NULL 制約) 列に対して、NULL マスクを選択しました。
 
 ![検証メカニズムのエラー](../../relational-databases/security/media/sql-static-data-masking/validation_mechanism_error_message.PNG)
 
 次の例のユーザーは、列が 1 つだけなのにグループ シャッフル マスクを選択しました。 グループ シャッフルには 2 つ以上の列が必要なので、警告が表示されます。 
 
 ![検証メカニズムの警告](../../relational-databases/security/media/sql-static-data-masking/validation_warning.PNG)
 
5. 完全なマスク構成を XML ファイルに保存して、後で使用することができます。  マスク機能の構成は、Azure SQL データベースとオンプレミスのデータベースで同じですが、保存される他のプロパティ (バックアップ ファイルのパスなど) にはわずかな違いがあります。 構成を保存するには、 **[Save Config]\(構成の保存\)** をクリックして、ファイル名を入力し、[保存] をクリックします。  ユーザーは、 **[Load Config]\(構成の読み込み\)** を使用して、既存の構成ファイルを後で読み込むことができます。列の数が多いテーブルには構成ファイルの使用をお勧めします。 
 
 ![[構成ファイル]](../../relational-databases/security/media/sql-static-data-masking/load_save_config.PNG)
 
6. 静的データ マスクでは、ユーザーの **[Documents]** フォルダーに [Static Data Masking] という名前のフォルダーが作成されて、ログ ファイルが格納されます。 ログ ファイルは、デバッグの目的に役立ちます。 ログ ファイルの名前は、構成ウィンドウの下部で示されます。 
  
 
7. (SQL Server のみ) オンプレミスのデータベースで静的データ マスクを使用すると、バックアップ/復元操作が実行されます。 **[Step 2:Clone .BAK file Location]\(ステップ 2: .BAK ファイルの場所の複製\)** では、バックアップ ファイルを格納するサーバー上の場所を指定します。 

## <a name="masking-functions"></a>マスク機能

### <a name="null-masking"></a>NULL マスク

NULL マスクでは、列のすべての値が NULL に置き換えられます。 列で NULL 値が許容されていない場合、静的データ マスク ツールはエラーを返します。 

### <a name="single-value-masking"></a>単一値マスク

単一値マスクでは、列のすべての値が 1 つの固定値に置き換えられます。この値はユーザーが指定します。 入力の形式は、選択した列の型が何であっても変換できるものでなければなりません。 値を指定するには、 **[構成...]** をクリックして、値を指定し、 **[OK]** をクリックします。 

![単一値マスクのパラメーター](../../relational-databases/security/media/sql-static-data-masking/single_value_parameter.PNG)


### <a name="shuffle-masking"></a>シャッフル マスク

列のすべての値が、新しい行にシャッフルされます。 新しいデータは生成されません。 シャッフル マスクでは、列の NULL エントリを保持するオプションが提供されます。 これを行うには、 **[構成]** をクリックして、[Maintain NULL positions]\(NULL の位置を保持する\) ボックスをオンにします。

![シャッフル マスクのパラメーター](../../relational-databases/security/media/sql-static-data-masking/shuffle_parameter.PNG)

シャッフル マスクで NULL 値の位置を保持しない場合と保持する場合の例を次に示します。


| 米国の社会保障番号 (マスク前) | 米国の社会保障番号 (マスク後、NULL エントリをシャッフルする) | 米国の社会保障番号 (マスク後、NULL エントリをシャッフルしない) |
| ------------- | ------------- | ------------- |
| 116-30-8733 | 612-72-1026 | 463-34-5535 |
| 140-38-9110 | NULL | 573-91-5137  |
| 209-36-1971 | 523-93-4176 | 140-38-9110 |
| NULL | 209-36-1971 | NULL |
| 463-34-5535 | 140-38-9110 | 116-30-8733  |
| 523-93-4176 | 463-34-5535 | 612-72-1026  |
| NULL | 573-91-5137 | NULL |
| 573-91-5137 | NULL | 523-93-4176 |
| 612-72-1026  | 116-30-8733  | 209-36-1971 |  

### <a name="group-shuffle-masking"></a>グループ シャッフル マスク
グループ シャッフルでは、複数の列がシャッフル グループにバインドされます。 シャッフル グループ内の列はまとめてシャッフルされます。 ユーザーは、 **[構成]** オプションを使用してシャッフル グループの名前を指定する必要があります。

![グループ シャッフル マスクのパラメーター](../../relational-databases/security/media/sql-static-data-masking/group_shuffle_parameter.PNG)

グループ シャッフルは同じテーブル内で行われます。複数のテーブルで同じシャッフル グループ名が使用されていても、2 つのグループ シャッフルは独立したアクションです。 グループに含まれる各列で、グループ名が同じである必要があります。 名前の大文字と小文字は区別されます。 同じテーブルで複数のシャッフル グループ (別の名前) を使用できます。 

### <a name="string-composite-masking"></a>文字列合成マスク

文字列合成マスクでは、パターンに従ってランダムな文字列が生成されます。 エントリが有効であるためには文字列が定義済みのパターンに従う必要があるように設計されています。 たとえば、米国の社会保障番号の形式は 123-45-6789 です。 ユーザーは、文字列合成マスクの構文を指定するパターンを、ダイアログ ボックスで入力する必要があります。

![文字列合成マスクのパラメーター](../../relational-databases/security/media/sql-static-data-masking/string_composite.PNG)

文字列合成マスクでは 3 つのパターン例が提供されており、クリックしてテストできます。 [Phone Number]\(電話番号\) をクリックすると、ランダムなアメリカの電話番号を生成するために必要な式が、パターン ボックスに自動的に設定されます。

![文字列合成マスクのパラメーターの例](../../relational-databases/security/media/sql-static-data-masking/string_composite_phone_example.PNG)

文字列合成マスクには高度なモードもあり、既存データのサブセクションをパターンによって生成された文字列で置き換えることができます。 文字列の置き換えられる部分は、正規表現のキャプチャ グループによって決定されます。 たとえば、メール アドレスのドメインを維持しながらユーザー名部分を置き換えたり、市外局番を維持して電話番号を置き換えたりすることができます。 正規表現について詳しくは、[こちら](https://docs.microsoft.com/dotnet/standard/base-types/regular-expression-language-quick-reference)をご覧ください。

![文字列合成マスクの高度なパラメーターの例](../../relational-databases/security/media/sql-static-data-masking/string_composite_advanced.PNG)

文字列合成マスクとその高度なモードは、[データ型](../../t-sql/data-types/data-types-transact-sql.md)が char、varchar、text、nchar、nvarchar、ntext である列に対してのみ使用できます。

## <a name="limitations"></a>制限事項 

静的データ マスクには、次のような制限があります。

- 静的データ マスクでは、[テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)を含むデータベースはサポートされません。

- 静的データ マスクでは、[メモリ最適化](../../relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables.md)テーブルはマスクされません。

- 静的データ マスクでは、[計算列](../../relational-databases/tables/specify-computed-columns-in-a-table.md)および [ID](../../t-sql/statements/create-table-transact-sql-identity-property.md) 列はマスクされません。

- 静的データ マスクでは、Azure SQL のハイパースケール データベースはサポートされません。

- 静的データ マスクでは、geometry および geography データ型はサポートされません。 

さらに、静的データ マスクでは、そのマスク機能に関して 3 つの制限があります。

- 静的データ マスクでは、[ヒストグラム統計](../../relational-databases/statistics/statistics.md)は更新されません。 そのため、静的データ マスクが完了した後、データベースのマスクされたコピーのヒストグラム統計情報に、機密データがまだ含まれる可能性があります。 [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) を実行してこの問題を解決することを検討してください。 

- 静的データ マスクでエラーが返った場合、すべてのマスク操作が中断されます。 データベースのコピーは削除されず、機密情報が含まれる可能性があります。 静的データ マスクでエラーが返った場合は、ユーザーにコピーを削除する責任があります。 

- (SQL Server のみ) 静的データ マスクが完了した後も、[データ ファイル](../../relational-databases/databases/database-files-and-filegroups.md)と[ログ ファイル](../../relational-databases/logs/the-transaction-log-sql-server.md)の未割り当てメモリ内に機密データが含まれる場合があります。 データ ファイルとログ ファイルに対するアクセス権が付与された場合、この機密データを 16 進エディターで取得できる可能性があります。

## <a name="see-also"></a>参照  
 [動的なデータ マスキング](../../relational-databases/security/dynamic-data-masking.md)   
 [SQL Database の静的データ マスクでの作業開始](https://azure.microsoft.com/documentation/articles/sql-database-static-data-masking-get-started/)  
