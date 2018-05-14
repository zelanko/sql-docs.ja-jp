---
title: 行フィルターを使用して動的なセキュリティを実装 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 157da34809a2ff7d9d5b3115eccfef1e386032eb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="supplemental-lesson---implement-dynamic-security-by-using-row-filters"></a>補足のレッスンで行フィルターを使用して動的なセキュリティを実装します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

この補足のレッスンでは、動的なセキュリティを実装する追加のロールを作成します。 動的なセキュリティには、現在ログオンしているユーザーのユーザー名またはログイン ID に基づいた行レベルのセキュリティが用意されています。 詳細については、「 [[ロール]](../analysis-services/tabular-models/roles-ssas-tabular.md)」 を参照してください。  
  
動的なセキュリティを実装するには、データ ソースとしてのモデルへの接続を作成し、モデル オブジェクトとデータを参照できるユーザーの Windows ユーザー名を含むテーブルを、モデルに追加する必要があります。 このチュートリアルで作成するモデルは Adventure Works Corp. のコンテキスト内にありますが、このレッスンを完了するには、自分のドメインのユーザーが含まれているテーブルを追加する必要があります。 追加するユーザー名のパスワードは必要ありません。 EmployeeSecurity テーブルでは、ユーザー独自のドメインからの小さなサンプルを使用して作成するには、が機能を使用する、貼り付け、Excel スプレッドシートから従業員データの貼り付けします。 実際のシナリオでは、モデルに追加するユーザー名が含まれたテーブルは通常、実際のデータベースのテーブル (たとえば、実際の dimEmployee テーブルなど) をデータ ソースとして使用します。  
  
動的なセキュリティを実装するには、 [USERNAME Function (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f) および [LOOKUPVALUE Function (DAX)](http://msdn.microsoft.com/en-us/73a51c4d-131c-4c33-a139-b1342d10caab)という 2 つの新しい DAX 関数を使用します。 行フィルター式に適用されるこれらの関数は、新しいロールで定義されています。 LOOKUPVALUE 関数を使用して、数式は EmployeeSecurity テーブルから値を指定し、USERNAME 関数にログオンしたユーザーのユーザー名を指定する値がこのロールに属していることを渡します。 ユーザーは、ロールの行フィルターによって指定されたデータのみを参照できます。 このシナリオでは、販売担当者がインターネット上で自分の販売区域の売上データのみを参照できるように指定します。  
  
この補足のレッスンを完了するには、一連の作業を行います。 この Adventure Works テーブル モデルに固有の作業が実際のシナリオに必ずしも適用されない場合には、そのように記載されています。 各作業には、作業の目的を表す追加情報が含まれています。  
  
このレッスンの推定所要時間: **30 分**  
  
## <a name="prerequisites"></a>前提条件  
この補足のレッスンのトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 この補足のレッスンの作業を実行する前に、前のレッスンをすべて完了している必要があります。  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>AW Internet Sales Tabular Model プロジェクトへの dimSalesTerritory テーブルの追加  
この Adventure Works のシナリオの動的セキュリティを実装するには、2 つの追加テーブルをモデルに追加する必要があります。 最初に追加するテーブルは、同じ AdventureWorksDW データベースの (販売区域としての) dimSalesTerritory です。 後でログオンしているユーザーが閲覧できる特定のデータを定義する SalesTerritory テーブルに行フィルターが適用されます。  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>dimSalesTerritory テーブルを追加するには  
  
1.  SSDT をクリックして、**モデル** メニューをクリックして**既存の接続**です。  
  
2.  **[既存の接続]** ダイアログ ボックスで **[Adventure Works DB from SQL]** データ ソース接続が選択されていることを確認し、 **[開く]** をクリックします。  
  
    [権限借用の資格情報] ダイアログ ボックスが表示された場合は、「レッスン 2: データの追加」で使用した権限借用の資格情報を入力します。  
  
3.  **[データのインポート方法の選択]** ページで、 **[インポートするデータをテーブルとビューの一覧から選択する]** が選択されていることを確認し、 **[次へ]** をクリックします。  
  
4.  **[テーブルとビューの選択]** ページで、 **DimSalesTerritory** テーブルをクリックします。  
  
5.  **[プレビューとフィルター]** をクリックします。  
  
6.  **SalesTerritoryAlternateKey** 列を選択解除して、 **[OK]** をクリックします。  
  
7.  **[テーブルとビューの選択]** ページで、 **[完了]** をクリックします。  
  
    新しいテーブルがモデル ワークスペースに追加されます。 オブジェクトとソースの DimSalesTerritory テーブルからのデータは、AW Internet Sales Tabular Model にインポートされます。  
  
9. テーブルのインポートが完了したら、 **[閉じる]** をクリックします。  

## <a name="add-a-table-with-user-name-data"></a>ユーザー名データを含むテーブルの追加  
AdventureWorksDW サンプル データベース内の dimEmployee テーブルには AdventureWorks ドメインのユーザーが含まれており、それらのユーザー名はご使用の環境に存在しないため、組織の実際のユーザーの小人数 (3 人) のサンプルが含まれたテーブルをモデルに作成する必要があります。 その後、これらのユーザーを新しいロールにメンバーとして追加します。 サンプルのユーザー名のパスワードは不要ですが、自分のドメインの実際の Windows ユーザー名が必要になります。  
  
#### <a name="to-add-an-employeesecurity-table"></a>EmployeeSecurity テーブルを追加するには  
  
1.  Microsoft Excel を開き、新しいワークシートを作成します。  
  
2.  ヘッダー行を含む次のテーブルをコピーし、ワークシートに貼り付けます。  

    ```
      |EmployeeId|SalesTerritoryId|FirstName|LastName|LoginId|  
      |---------------|----------------------|--------------|-------------|------------|  
      |1|2|<user first name>|<user last name>|\<domain\username>|  
      |1|3|<user first name>|<user last name>|\<domain\username>|  
      |2|4|<user first name>|<user last name>|\<domain\username>|  
      |3|5|<user first name>|<user last name>|\<domain\username>|  
    ```

3.  名前と、組織内の 3 人のユーザーのログイン id で、名、姓、名、およびドメイン \ ユーザー名を置き換えます。 EmployeeId 1 の最初の 2 つの行に同じユーザーを配置します。 これは、このユーザーが 1 つ以上の販売区域に属していることを示します。 EmployeeId と SalesTerritoryId フィールドはそのままにします。  
  
4.  ワークシートとして保存**SampleEmployee**です。  
  
5.  ワークシート内のすべての従業員に関するデータをヘッダーを含むセルを選択し、選択したデータを右クリックし、をクリックして**コピー**です。  
  
6.  SSDT をクリックして、**編集** メニューをクリックして**貼り付け**です。  
  
    貼り付けは淡色表示された場合、は、モデル デザイナー ウィンドウの任意のテーブルの任意の列をクリックしてからやり直してください。  
  
7.  **貼り付けプレビュー**ダイアログ ボックスで、**テーブル名**、型**EmployeeSecurity**です。  
  
8.  **貼り付けるデータ**データを含むすべてのユーザー データと SampleEmployee ワークシートからヘッダーを確認してください。  
  
9. **[先頭の行を列見出しとして使用する]** がオンであることを確認し、 **[OK]** をクリックします。  
  
    SampleEmployee ワークシートからコピーした従業員データを含む EmployeeSecurity をという名前の新しいテーブルが作成されます。  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成します。  
すべて FactInternetSales、DimGeography、および DimSalesTerritory テーブルには、共通の列、SalesTerritoryId が含まれています。 DimSalesTerritory テーブルの [SalesTerritoryId] 列には、販売区域ごとの別の id 値が含まれています。  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成するには  
  
1.  ダイアグラム ビューで、モデル デザイナーでの**DimGeography**テーブルをクリックし、保持、 **SalesTerritoryId**  列にカーソルをドラッグ、 **SalesTerritoryId**内の列、 **DimSalesTerritory**テーブル、および離します。  
  
2.  **FactInternetSales**テーブルをクリックし、保持、 **SalesTerritoryId**  列にカーソルをドラッグし、 **SalesTerritoryId**内の列、 **DimSalesTerritory**テーブル、および離します。  
  
    このリレーションシップのアクティブなプロパティが False で、アクティブになっていないことを確認します。 これは、FactInternetSales テーブルは、メジャーで使用されている別のアクティブなリレーションシップを既に持っているためです。  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションから EmployeeSecurity テーブルを非表示します。  
このタスクでは非表示にする EmployeeSecurity テーブルでは、クライアント アプリケーションのフィールド リストに表示されないようにします。 テーブルを非表示にしても、セキュリティで保護されるわけではないことに注意してください。 わかっている場合、ユーザーは EmployeeSecurity テーブル データを照会まだできますか。 そのデータのいずれかのクエリを実行できることを防ぐ EmployeeSecurity テーブルのデータを保護するためには、後のタスクでフィルターを適用します。  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションから EmployeeSecurity テーブルを非表示にするには  
  
-   モデル デザイナーのダイアグラム ビューで、 **Employee** テーブルの見出しを右クリックし、 **[クライアント ツールで非表示にする]** をクリックします。  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールの作成  
この作業では、新しいユーザー ロールを作成します。 このロール定義の DimSalesTerritory テーブルのどの行がユーザーに表示された行フィルターが含まれます。 DimSalesTerritory に関連するその他のすべてのテーブルに一対多リレーションシップの方向にフィルターが適用されます。 ロールのメンバーであるすべてのユーザーがクエリ可能なされない EmployeeSecurity テーブル全体をセキュリティで保護する単純なフィルターも適用されます。  
  
> [!NOTE]  
> このレッスンで作成する Sales Employees by Territory ロールによって、メンバーが参照 (またはクエリを実行) できるデータは、自分が属する販売区域の売上データのみに制限されます。 場合は、ユーザーを追加するメンバーとして、Sales Employees by Territory ロールでロールのメンバーが作成されるようにも存在する[レッスン 11: ロールの作成](../analysis-services/lesson-11-create-roles.md)、アクセス許可の組み合わせが表示されます。 あるユーザーが複数のロールのメンバーである場合、各ロールに対して定義された権限と行フィルターは累積されます。 つまり、ロールを組み合わせることでユーザーの権限は引き上げられます。  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールを作成するには  
  
1.  SSDT をクリックして、**モデル** メニューをクリックして**ロール**です。  
  
2.  **ロール マネージャー**をクリックして**新規**です。  
  
    "なし" 権限を設定された新しいロールがリストに追加されます。  
  
3.  新しいロールをクリックし、 **[名前]** 列で、ロールの名前を「 **Sales Employees by Territory**」に変更します。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、**[読み取り]** 権限を選択します。  
  
5.  **[メンバー]** タブをクリックし、 **[追加]** をクリックします。  
  
6.  **ユーザーまたはグループ**ダイアログ ボックスで、**を選択するオブジェクト名を入力**、EmployeeSecurity テーブルを作成するときに使用した最初のサンプル ユーザー名を入力します。 **[名前の確認]** をクリックしてユーザー名が有効であることを確認し、 **[OK]** をクリックします。  
  
    名前の追加の他のサンプル ユーザー EmployeeSecurity テーブルを作成するときに使用した、この手順を繰り返します。  
  
7.  **[行フィルター]** タブをクリックします。  
  
8.  **EmployeeSecurity**表で、 **DAX フィルター**列で、次の数式を入力します。  
  
    ```
      =FALSE()  
    ```
  
    この数式は、false ブール条件にすべての列を解決することを指定しますしたがって、EmployeeSecurity テーブルの列が照会できるなし Sales Employees のメンバー by Territory ユーザー ロール。  
  
9. **DimSalesTerritory**テーブルで、次の数式を入力します。  

    ```  
    ='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 
      'Employee Security'[Login Id], USERNAME(), 
      'Employee Security'[Sales Territory Id], 
      'Sales Territory'[Sales Territory Id]) 
    ```
  
    この数式では、LOOKUPVALUE 関数は、EmployeeSecurity [LoginId] 現在ログオンしている Windows ユーザー名と同じであり、EmployeeSecurity [SalesTerritoryId] は、同じ DimSalesTerritory [SalesTerritoryId] として、DimEmployeeSecurity [SalesTerritoryId] 列のすべての値を返します。  
  
    Id は、LOOKUPVALUE で返された販売区域のセットを使用し、DimSalesTerritory テーブルに表示される行を制限できます。 LOOKUPVALUE 関数によって返される id セット内の行の SalesTerritoryID がここでは行のみが表示されます。  
  
10. ロール マネージャーで、をクリックして**Ok**です。  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールのテスト  
このタスクでは SSDT での Excel 機能で、分析を使用して by Territory ユーザー ロール Sales Employees の有効性をテストします。 EmployeeSecurity テーブルと、ロールのメンバーとして追加したユーザー名のいずれかを指定します。 このユーザー名は、Excel とモデルの間に作成された接続で有効なユーザー名として使用されます。  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールをテストするには  
  
1.  SSDT をクリックして、**モデル** メニューをクリックして**Excel で分析**です。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、 **[その他の Windows ユーザー]** をクリックし、 **[参照]** をクリックします。  
  
3.  **ユーザーまたはグループ**ダイアログ ボックスで、**を選択するオブジェクト名を入力**EmployeeSecurity テーブルに含まれるユーザー名のいずれかを入力し、クリックして**名前の確認**.  
  
4.  **[OK]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを閉じ、 **[OK]** をクリックして **[Excel で分析]** ダイアログ ボックスを閉じます。  
  
    Excel で新しいブックが開きます。 ピボット テーブルが自動的に作成します。 ピボット テーブル フィールド リストには、ほとんど、新しいモデルで使用可能なデータ フィールドにはが含まれています。  
  
    EmployeeSecurity テーブルがピボット テーブル フィールド リストに表示されないことを確認します。 これは、前の作業でクライアント ツールからこのテーブルを非表示にすることを選択したためです。  
  
5.  **フィールド**一覧**∑ Internet Sales** (メジャー) を選択、 **InternetTotalSales**メジャーです。 メジャーは **値** フィールドに入力されます。  
  
6.  選択、 **SalesTerritoryId**列から、 **DimSalesTerritory**テーブル。 列は **行ラベル** フィールドに入力されます。  
  
    使用した有効なユーザー名が属している 1 つの地域のインターネット販売成績のみが表示されていることに注意してください。 別の列を選択した場合たとえば、市区町村、DimGeography とテーブルから行ラベル フィールドに、有効なユーザーが属する販売区域の都市のみが表示されます。  
  
    このユーザーは、自分が属する区域以外の区域のインターネット販売データを参照したり、クエリを実行することはできません。これは、Sales Employees by Territory ユーザー ロールで Sales Territory テーブルに定義された行フィルターによって、他の販売区域に関連するすべてのデータが効果的に保護されているためです。  
  
## <a name="see-also"></a>参照  
[USERNAME Function (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)  
[LOOKUPVALUE Function (DAX)](http://msdn.microsoft.com/en-us/73a51c4d-131c-4c33-a139-b1342d10caab)  
[CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
