---
title: "行フィルターを使用した動的なセキュリティの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 8bf03c45-caf5-4eda-9314-e4f8f24a159f
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 行フィルターを使用した動的なセキュリティの実装
この補足のレッスンでは、動的なセキュリティを実装する追加のロールを作成します。 動的なセキュリティには、現在ログオンしているユーザーのユーザー名またはログイン ID に基づいた行レベルのセキュリティが用意されています。 詳細については、「[ロール (SSAS テーブル)](../analysis-services/tabular-models/roles-ssas-tabular.md)」 を参照してください。  
  
動的なセキュリティを実装するには、データ ソースとしてのモデルへの接続を作成し、モデル オブジェクトとデータを参照できるユーザーの Windows ユーザー名を含むテーブルを、モデルに追加する必要があります。 このチュートリアルで作成するモデルは Adventure Works Corp. のコンテキスト内にありますが、このレッスンを完了するには、自分のドメインのユーザーが含まれているテーブルを追加する必要があります。 追加するユーザー名のパスワードは必要ありません。 自分のドメインの小人数のサンプル ユーザーを使用して Employee Security テーブルを作成するには、貼り付け機能を使用して、Excel スプレッドシートから従業員データを貼り付けます。 実際のシナリオでは、モデルに追加するユーザー名が含まれたテーブルは通常、実際のデータベースのテーブル (たとえば、実際の dimEmployee テーブルなど) をデータ ソースとして使用します。  
  
動的なセキュリティを実装するには、[USERNAME Function (DAX)](http://msdn.microsoft.com/ja-jp/22dddc4b-1648-4c89-8c93-f1151162b93f) および [LOOKUPVALUE Function (DAX)](http://msdn.microsoft.com/ja-jp/73a51c4d-131c-4c33-a139-b1342d10caab) という 2 つの新しい DAX 関数を使用します。 行フィルター式に適用されるこれらの関数は、新しいロールで定義されています。 数式では LOOKUPVALUE 関数を使用して Employee Security テーブルの値を指定し、その値を USERNAME 関数に渡します。この関数は、ログオンしているユーザーのユーザー名がこのロールに属することを指定します。 ユーザーは、ロールの行フィルターによって指定されたデータのみを参照できます。 このシナリオでは、販売担当者がインターネット上で自分の販売区域の売上データのみを参照できるように指定します。  
  
この補足のレッスンを完了するには、一連の作業を行います。 この Adventure Works テーブル モデルに固有の作業が実際のシナリオに必ずしも適用されない場合には、そのように記載されています。 各作業には、作業の目的を表す追加情報が含まれています。  
  
このレッスンの推定所要時間: **30 分**  
  
## 前提条件  
この補足のレッスンのトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 この補足のレッスンの作業を実行する前に、前のレッスンをすべて完了している必要があります。  
  
## AW Internet Sales Tabular Model プロジェクトへの dimSalesTerritory テーブルの追加  
この Adventure Works のシナリオの動的セキュリティを実装するには、2 つの追加テーブルをモデルに追加する必要があります。 最初に追加するテーブルは、同じ AdventureWorksDW データベースの (販売区域としての) dimSalesTerritory です。 後から、ログオンしているユーザーが参照できる特定のデータを定義する行フィルターを Sales Territory テーブルに適用します。  
  
#### dimSalesTerritory テーブルを追加するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[既存の接続]**をクリックします。  
  
2.  **[既存の接続]** ダイアログ ボックスで **[Adventure Works DB from SQL]** データ ソース接続が選択されていることを確認し、**[開く]** をクリックします。  
  
    [権限借用の資格情報] ダイアログ ボックスが表示された場合は、「レッスン 2: データの追加」で使用した権限借用の資格情報を入力します。  
  
3.  **[データのインポート方法の選択]** ページで、**[インポートするデータをテーブルとビューの一覧から選択する]** が選択されていることを確認し、**[次へ]** をクリックします。  
  
4.  **[テーブルとビューの選択]** ページで、**DimSalesTerritory** テーブルをクリックします。  
  
5.  [表示名] 列に「**Sales Territory**」と入力します。  
  
6.  **[プレビューとフィルター]** をクリックします。  
  
7.  **SalesTerritoryAlternateKey** 列を選択解除して、**[OK]** をクリックします。  
  
8.  **[テーブルとビューの選択]** ページで、**[完了]** をクリックします。  
  
    新しいテーブルがモデル ワークスペースに追加されます。 ソースの dimSalesTerritory テーブルのオブジェクトおよびデータが AW Internet Sales Tabular Model の新しい Sales Territory テーブルにインポートされます。  
  
9. テーブルのインポートが完了したら、**[閉じる]** をクリックします。  
  
## 列の表示名の指定  
この作業では表示名を指定して、Sales Territory テーブルの列の名前を変更します。 テーブルや列の表示名の指定は必ずしも必要ではありません。ただし、名前を変更することで、モデル デザイナー内のモデル プロジェクトでも、またクライアント アプリケーションのフィールド リストでユーザーがモデル オブジェクトやデータを参照する際にも、移動が行いやすくなります。  
  
#### Sales Territory テーブル内の列の名前を変更するには  
  
-   モデル デザイナーで、**Sales Territory** テーブル内の列の名前を次のように変更します。  
  
    **Sales Territory**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |SalesTerritoryKey|Sales Territory Id|  
    |SalesTerritoryRegion|Sales Territory Region|  
    |SalesTerritoryCountry|Sales Territory Country|  
    |SalesTerritoryGroup|Sales Territory Group|  
  
## ユーザー名データを含むテーブルの追加  
AdventureWorksDW サンプル データベース内の dimEmployee テーブルには AdventureWorks ドメインのユーザーが含まれており、それらのユーザー名はご使用の環境に存在しないため、組織の実際のユーザーの小人数 (3 人) のサンプルが含まれたテーブルをモデルに作成する必要があります。 その後、これらのユーザーを新しいロールにメンバーとして追加します。 サンプルのユーザー名のパスワードは不要ですが、自分のドメインの実際の Windows ユーザー名が必要になります。  
  
#### Employee Security テーブルを追加するには  
  
1.  Microsoft Excel を開き、新しいワークシートを作成します。  
  
2.  ヘッダー行を含む次のテーブルをコピーし、ワークシートに貼り付けます。  
  
    |Employee Id|Sales Territory Id|First Name|Last Name|ログイン ID|  
    |---------------|----------------------|--------------|-------------|------------|  
    |1|2|<user first name>|<user last name>|\<ドメイン\ユーザー名>|  
    |1|3|<user first name>|<user last name>|\<ドメイン\ユーザー名>|  
    |2|4|<user first name>|<user last name>|\<ドメイン\ユーザー名>|  
    |3|5|<user first name>|<user last name>|\<ドメイン\ユーザー名>|  
  
3.  新しいワークシートで、名、姓、および domain\username を組織の 3 人のユーザーの名前とログイン ID に置き換えます。 先頭の 2 つの行に、Employee Id 1 の同じユーザーを配置します。 これは、このユーザーが 1 つ以上の販売区域に属していることを示します。 Employee Id フィールドと Sales Territory Id フィールドはそのままにします。  
  
4.  ワークシートを **Sample Employee** として保存します。  
  
5.  ワークシートで、従業員データを含むすべてのセルをヘッダーと共に選択し、選択したデータを右クリックし、**[コピー]** をクリックします。  
  
6.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で **[編集]** メニューをクリックし、**[貼り付け]** をクリックします。  
  
    [貼り付け] がグレー表示されている場合は、モデル デザイナー ウィンドウの任意のテーブルの任意の列をクリックし、**[編集]** メニューの **[貼り付け]** をクリックします。  
  
7.  **[貼り付けプレビュー]** ダイアログ ボックスの **[テーブル名]** に、「**Employee Security**」と入力します。  
  
8.  **[貼り付けるデータ]** で、Sample Employee ワークシートのすべてのユーザー データとヘッダーが含まれていることを確認します。  
  
9. **[先頭の行を列見出しとして使用する]** がオンであることを確認し、**[OK]** をクリックします。  
  
    Sample Employee ワークシートからコピーした従業員データを含む、Employee Security という名前の新しいテーブルが作成されます。  
  
## Internet Sales、Geography、および Sales Territory テーブル間のリレーションシップの作成  
Internet Sales、Geography、および Sales Territory テーブルはすべて、共通の列である Sales Territory Id を含みます。 Sales Territory テーブルの Sales Territory Id 列には、販売区域ごとに異なる ID の値が含まれています。  
  
#### Internet Sales、Geography、および Sales Territory テーブル間のリレーションシップを作成するには  
  
1.  モデル デザイナーのダイアグラム ビューの **Geography** テーブルで、**[Sales Territory Id]** 列をクリックし、そのままカーソルを **Sales Territory** テーブル内の **Sales Territory Id** 列にドラッグして離します。  
  
2.  **Internet Sales** テーブルで、**[Sales Territory Id]** 列をクリックし、そのままカーソルを **Sales Territory** テーブル内の **Sales Territory Id** 列にドラッグして離します。  
  
    このリレーションシップの Active プロパティは False であり、非アクティブであることを意味します。 これは、Internet Sales テーブルにはメジャーで使用されている別のアクティブなリレーションシップが既にあるためです。  
  
## クライアント アプリケーションで Employee Security テーブルを非表示にする  
この作業では、Employee Security テーブルを非表示にして、クライアント アプリケーションのフィールド リストに表示されないようにします。 テーブルを非表示にしても、セキュリティで保護されるわけではないことに注意してください。 方法を知っていれば、ユーザーは引き続き Employee Security テーブル データのクエリを実行できます。 Employee Security テーブルのデータをセキュリティで保護し、ユーザーがデータに対してクエリを実行できないようにするには、この後の作業でフィルターを適用します。  
  
#### クライアント アプリケーションで Employee テーブルを非表示にするには  
  
-   モデル デザイナーのダイアグラム ビューで、**Employee** テーブルの見出しを右クリックし、**[クライアント ツールで非表示にする]** をクリックします。  
  
## Sales Employees by Territory ユーザー ロールの作成  
この作業では、新しいユーザー ロールを作成します。 このロールには、Sales Territory テーブル内のどの行がユーザーに表示されるかを定義する行フィルターが含まれます。 このフィルターは、一対多のリレーションシップの方向で、Sales Territory に関連する他のすべてのテーブルに適用されます。 また、ロールのメンバーであるユーザーがクエリを実行できないように Employee Security テーブル全体を保護する簡単なフィルターも追加します。  
  
> [!NOTE]  
> このレッスンで作成する Sales Employees by Territory ロールによって、メンバーが参照 (またはクエリを実行) できるデータは、自分が属する販売区域の売上データのみに制限されます。 Sales Employees by Territory ロールにメンバーとして追加したユーザーが、「[レッスン 12: ロールの作成](../analysis-services/lesson-12-create-roles.md)」で作成したロールのメンバーでもある場合、権限は組み合わせとなります。 あるユーザーが複数のロールのメンバーである場合、各ロールに対して定義された権限と行フィルターは累積されます。 つまり、ロールを組み合わせることでユーザーの権限は引き上げられます。  
  
#### Sales Employees by Territory ユーザー ロールを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で **[モデル]** メニューをクリックし、**[ロール]** をクリックします。  
  
2.  **[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
    "なし" 権限を設定された新しいロールがリストに追加されます。  
  
3.  新しいロールをクリックし、**[名前]** 列で、ロールの名前を「**Sales Employees by Territory**」に変更します。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、**[読み取り]** 権限を選択します。  
  
5.  **[メンバー]** タブをクリックし、**[追加]** をクリックします。  
  
6.  **[ユーザーまたはグループの選択]** ダイアログ ボックスの **[選択するオブジェクト名を入力してください]** に、Employee Security テーブルの作成で使用した最初のサンプル ユーザー名を入力します。 **[名前の確認]** をクリックしてユーザー名が有効であることを確認し、**[OK]** をクリックします。  
  
    この手順を繰り返して、Employee Security テーブルの作成で使用した他のサンプル ユーザー名を追加します。  
  
7.  **[行フィルター]** タブをクリックします。  
  
8.  **Employee Security** テーブルについて、**[DAX フィルター]** 列に次の式を入力します。  
  
    **=FALSE()**  
  
    数式の入力が終了したら、Enter キーを押します。  
  
    この数式は、すべての列がブール条件 false に解決されることを指定します。このため、Employee Security テーブルで Sales Employees by Territory ユーザー ロールのメンバーがクエリを実行できる列はありません。  
  
9. **Sales Territory** テーブルには、次の数式を入力します。  
  
    **='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 'Employee Security'[Login Id], USERNAME(), 'Employee Security'[Sales Territory Id], 'Sales Territory'[Sales Territory Id])**  
  
    数式の入力が終了したら、Enter キーを押します。  
  
    この数式では、LOOKUPVALUE 関数によって、現在ログオンしている Windows ユーザー名と同じ Employee Security[Login Id] を持つ Employee Security[Sales Territory Id] 列のすべての値が返されます。Employee Security[Sales Territory Id] は Sales Territory[Sales Territory Id] と同じです。  
  
    LOOKUPVALUE によって返された一連の Sales Territory ID を使用して、Sales Territory テーブルに表示される行が制限されます。 LOOKUPVALUE 関数で返された一連の ID と Sales Territory ID が一致する行のみが表示されます。  
  
10. [ロール マネージャー] ダイアログ ボックスで、**[OK]** をクリックします。  
  
## Sales Employees by Territory ユーザー ロールのテスト  
この作業では、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] の [Excel で分析] 機能を使用して、Sales Employees by Territory ユーザー ロールの有効性をテストできます。 Employee Security テーブルに追加したロールのメンバーのうちの、いずれかのユーザー名を指定します。 このユーザー名は、Excel とモデルの間に作成された接続で有効なユーザー名として使用されます。  
  
#### Sales Employees by Territory ユーザー ロールをテストするには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で、**[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、**[その他の Windows ユーザー]** をクリックし、**[参照]** をクリックします。  
  
3.  **[ユーザーまたはグループの選択]** ダイアログ ボックスの **[選択するオブジェクト名を入力してください]** に、Employee テーブルに追加したいずれかのユーザー名を入力し、**[名前の確認]** をクリックします。  
  
4.  **[OK]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを閉じ、**[OK]** をクリックして **[Excel で分析]** ダイアログ ボックスを閉じます。  
  
    Excel で新しいブックが開きます。 ピボット テーブルが自動的に作成されます。 [ピボットテーブルのフィールド リスト] には、新しいモデルで使用できるほとんどのデータ フィールドが表示されます。  
  
    Employee Security テーブルはピボットテーブルのフィールド リストに表示されないことに注意してください。 これは、前の作業でクライアント ツールからこのテーブルを非表示にすることを選択したためです。  
  
5.  **[ピボットテーブル フィールド]** の一覧の **∑ Internet Sales** (メジャー) で、**Internet Total Sales** メジャーを選択します。 メジャーは**値**フィールドに入力されます。  
  
6.  **[ピボットテーブル フィールド]** の一覧で、**Sales Territory** テーブルの **Sales Territory Id** 列を選択します。 列は**行ラベル** フィールドに入力されます。  
  
    使用した有効なユーザー名が属している 1 つの地域のインターネット販売成績のみが表示されていることに注意してください。 たとえば Geography テーブルの City など、別の列を行ラベル フィールドとして選択すると、有効なユーザーが属する販売区域の都市のみが表示されます。  
  
    このユーザーは、自分が属する区域以外の区域のインターネット販売データを参照したり、クエリを実行することはできません。これは、Sales Employees by Territory ユーザー ロールで Sales Territory テーブルに定義された行フィルターによって、他の販売区域に関連するすべてのデータが効果的に保護されているためです。  
  
## 参照  
[USERNAME 関数 (DAX)](http://msdn.microsoft.com/ja-jp/22dddc4b-1648-4c89-8c93-f1151162b93f)  
[LOOKUPVALUE 関数 (DAX)](http://msdn.microsoft.com/ja-jp/73a51c4d-131c-4c33-a139-b1342d10caab)  
[CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/ja-jp/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
