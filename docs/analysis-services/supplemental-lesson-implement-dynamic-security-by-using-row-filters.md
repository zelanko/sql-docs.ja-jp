---
title: 行フィルターを使用して動的なセキュリティの実装 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed672aedc62c9521fe475589de0a7aa9ac935614
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984390"
---
# <a name="supplemental-lesson---implement-dynamic-security-by-using-row-filters"></a>補足のレッスン - 動的なセキュリティを実装する行フィルターを使用します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

この補足のレッスンでは、動的なセキュリティを実装する追加のロールを作成します。 動的なセキュリティには、現在ログオンしているユーザーのユーザー名またはログイン ID に基づいた行レベルのセキュリティが用意されています。 詳細については、「 [[ロール]](../analysis-services/tabular-models/roles-ssas-tabular.md)」 を参照してください。  
  
動的なセキュリティを実装するには、データ ソースとしてのモデルへの接続を作成し、モデル オブジェクトとデータを参照できるユーザーの Windows ユーザー名を含むテーブルを、モデルに追加する必要があります。 このチュートリアルで作成するモデルは Adventure Works Corp. のコンテキスト内にありますが、このレッスンを完了するには、自分のドメインのユーザーが含まれているテーブルを追加する必要があります。 追加するユーザー名のパスワードは必要ありません。 独自のドメインからユーザーの小規模なサンプルでは、EmployeeSecurity テーブルを作成するには機能を使用する、貼り付け、Excel スプレッドシートから従業員データの貼り付けします。 実際のシナリオでは、モデルに追加するユーザー名が含まれたテーブルは通常、実際のデータベースのテーブル (たとえば、実際の dimEmployee テーブルなど) をデータ ソースとして使用します。  
  
動的なセキュリティを実装するには、[USERNAME Function (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f) および [LOOKUPVALUE Function (DAX)](http://msdn.microsoft.com/73a51c4d-131c-4c33-a139-b1342d10caab) という 2 つの新しい DAX 関数を使用します。 行フィルター式に適用されるこれらの関数は、新しいロールで定義されています。 LOOKUPVALUE 関数を使用して、この数式は EmployeeSecurity テーブルの値を指定しにログオンしたユーザーのユーザー名を指定する USERNAME 関数に値がこのロールに属していることを渡します。 ユーザーは、ロールの行フィルターによって指定されたデータのみを参照できます。 このシナリオでは、販売担当者がインターネット上で自分の販売区域の売上データのみを参照できるように指定します。  
  
この補足のレッスンを完了するには、一連の作業を行います。 この Adventure Works テーブル モデルに固有の作業が実際のシナリオに必ずしも適用されない場合には、そのように記載されています。 各作業には、作業の目的を表す追加情報が含まれています。  
  
このレッスンの推定所要時間: **30 分**  
  
## <a name="prerequisites"></a>前提条件  
この補足のレッスンのトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 この補足のレッスンの作業を実行する前に、前のレッスンをすべて完了している必要があります。  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>AW Internet Sales Tabular Model プロジェクトへの dimSalesTerritory テーブルの追加  
この Adventure Works のシナリオの動的セキュリティを実装するには、2 つの追加テーブルをモデルに追加する必要があります。 最初に追加するテーブルは、同じ AdventureWorksDW データベースの (販売区域としての) dimSalesTerritory です。 ログオンしたユーザーが参照できる特定のデータを定義する、SalesTerritory テーブルに行フィルターを後で適用されます。  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>dimSalesTerritory テーブルを追加するには  
  
1.  SSDT で、**モデル** メニューをクリック**既存の接続**します。  
  
2.  **[既存の接続]** ダイアログ ボックスで **[Adventure Works DB from SQL]** データ ソース接続が選択されていることを確認し、 **[開く]** をクリックします。  
  
    [権限借用の資格情報] ダイアログ ボックスが表示された場合は、「レッスン 2: データの追加」で使用した権限借用の資格情報を入力します。  
  
3.  **[データのインポート方法の選択]** ページで、 **[インポートするデータをテーブルとビューの一覧から選択する]** が選択されていることを確認し、 **[次へ]** をクリックします。  
  
4.  **[テーブルとビューの選択]** ページで、 **DimSalesTerritory** テーブルをクリックします。  
  
5.  **[プレビューとフィルター]** をクリックします。  
  
6.  **SalesTerritoryAlternateKey** 列を選択解除して、 **[OK]** をクリックします。  
  
7.  **[テーブルとビューの選択]** ページで、 **[完了]** をクリックします。  
  
    新しいテーブルがモデル ワークスペースに追加されます。 オブジェクトおよびデータ ソースの DimSalesTerritory テーブルは、し、AW Internet Sales Tabular Model にインポートされます。  
  
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

3.  名前と、組織内の 3 つのユーザーのログイン id では、名、姓、名、および domain \username を置き換えます。 EmployeeId 1 の最初の 2 つの行で同じユーザーを配置します。 これは、このユーザーが 1 つ以上の販売区域に属していることを示します。 そのまま、EmployeeId と SalesTerritoryId フィールド。  
  
4.  ワークシートとして保存**SampleEmployee**します。  
  
5.  ワークシート内のすべてのヘッダーを含む、従業員データを含むセルを選択し、選択したデータを右クリックし、順にクリックします**コピー**します。  
  
6.  SSDT で、**編集** メニューをクリック**貼り付け**します。  
  
    貼り付けがグレーの場合、モデル デザイナー ウィンドウで任意のテーブルの任意の列をクリックします。 もう一度やり直してください。  
  
7.  **貼り付けプレビュー**  ダイアログ ボックスで**テーブル名**、型**EmployeeSecurity**します。  
  
8.  **貼り付けるデータ**データを含むすべてのユーザー データと SampleEmployee ワークシートからヘッダーを確認します。  
  
9. **[先頭の行を列見出しとして使用する]** がオンであることを確認し、 **[OK]** をクリックします。  
  
    SampleEmployee ワークシートからコピーした従業員データを含む、EmployeeSecurity という名前の新しいテーブルが作成されます。  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成します。  
FactInternetSales、DimGeography、および DimSalesTerritory テーブルすべてでは、共通の列、SalesTerritoryId を含みます。 DimSalesTerritory テーブルの SalesTerritoryId 列には、販売区域ごとのさまざまな Id 値が含まれています。  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成するには  
  
1.  ダイアグラム ビューで、モデル デザイナーでの**DimGeography**テーブルをクリックし、保持、 **SalesTerritoryId**  列にカーソルをドラッグし、 **SalesTerritoryId**内の列、 **DimSalesTerritory**テーブル、および離します。  
  
2.  **FactInternetSales**テーブルをクリックし、保持、 **SalesTerritoryId**  列にカーソルをドラッグし、 **SalesTerritoryId**内の列、 **DimSalesTerritory**テーブル、および離します。  
  
    このリレーションシップの Active プロパティが False で、アクティブになっていないことを確認します。 FactInternetSales テーブルが既に別のアクティブなリレーションシップのメジャーで使用されているためにです。  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションで EmployeeSecurity テーブルを非表示にします。  
このタスクでは非表示にする、EmployeeSecurity テーブルでは、クライアント アプリケーションのフィールド リストに表示されないようにします。 テーブルを非表示にしても、セキュリティで保護されるわけではないことに注意してください。 わかっている場合、ユーザーは EmployeeSecurity テーブル データをクエリでもできますか。 ユーザーに対して、そのデータのクエリを実行できることができないように、EmployeeSecurity テーブル データを保護するためには、後のタスクでのフィルターが適用されます。  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションで EmployeeSecurity テーブルを非表示にするには  
  
-   モデル デザイナーのダイアグラム ビューで、 **Employee** テーブルの見出しを右クリックし、 **[クライアント ツールで非表示にする]** をクリックします。  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールの作成  
この作業では、新しいユーザー ロールを作成します。 このロールは、DimSalesTerritory テーブルの行がユーザーに表示を定義する行フィルターが含まれます。 DimSalesTerritory に関連するその他のすべてのテーブルと一対多リレーションシップの方向にフィルターが適用されます。 ロールのメンバーであるすべてのユーザーがクエリを実行できる EmployeeSecurity テーブル全体をセキュリティで保護する単純なフィルターも適用されます。  
  
> [!NOTE]  
> このレッスンで作成する Sales Employees by Territory ロールによって、メンバーが参照 (またはクエリを実行) できるデータは、自分が属する販売区域の売上データのみに制限されます。 追加する場合、ユーザーをメンバーとして、Sales Employees by Territory ロールで作成したロールのメンバーにも存在する[レッスン 11: ロールの作成](../analysis-services/lesson-11-create-roles.md)、アクセス許可の組み合わせが表示されます。 あるユーザーが複数のロールのメンバーである場合、各ロールに対して定義された権限と行フィルターは累積されます。 つまり、ロールを組み合わせることでユーザーの権限は引き上げられます。  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールを作成するには  
  
1.  SSDT で、**モデル** メニューをクリック**ロール**します。  
  
2.  **ロール マネージャー**、 をクリックして**新規**します。  
  
    "なし" 権限を設定された新しいロールがリストに追加されます。  
  
3.  新しいロールをクリックし、 **[名前]** 列で、ロールの名前を「 **Sales Employees by Territory**」に変更します。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、**[読み取り]** 権限を選択します。  
  
5.  **[メンバー]** タブをクリックし、 **[追加]** をクリックします。  
  
6.  **[ユーザーまたはグループ**] ダイアログ ボックスで**を選択するオブジェクト名を入力します。**、EmployeeSecurity テーブルを作成するときに使用した最初のサンプル ユーザー名を入力します。 **[名前の確認]** をクリックしてユーザー名が有効であることを確認し、 **[OK]** をクリックします。  
  
    その他のサンプル ユーザー名を追加、EmployeeSecurity テーブルの作成時に使用した、この手順を繰り返します。  
  
7.  **[行フィルター]** タブをクリックします。  
  
8.  **EmployeeSecurity**テーブル、 **DAX フィルター**列で、次の数式を入力します。  
  
    ```
      =FALSE()  
    ```
  
    この数式は、すべての列が false ブール条件に解決されることを指定しますそのため、EmployeeSecurity テーブルの列照会できますありません Sales Employees のメンバーによって by Territory ユーザー ロール。  
  
9. **DimSalesTerritory**テーブルで、次の数式を入力します。  

    ```  
    ='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 
      'Employee Security'[Login Id], USERNAME(), 
      'Employee Security'[Sales Territory Id], 
      'Sales Territory'[Sales Territory Id]) 
    ```
  
    この数式では、LOOKUPVALUE 関数は、EmployeeSecurity [LoginId] 現在ログオンしている Windows ユーザー名と同じであり、EmployeeSecurity [SalesTerritoryId] が DimEmployeeSecurity [SalesTerritoryId] 列のすべての値を返します、。DimSalesTerritory [SalesTerritoryId] と同じです。  
  
    LOOKUPVALUE によって返された Id の販売区域のセットは、DimSalesTerritory テーブルに表示される行を制限する、使用されます。 行の SalesTerritoryID が LOOKUPVALUE 関数によって返される id セット内にある行のみが表示されます。  
  
10. ロール マネージャー をクリックして**Ok**します。  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールのテスト  
このタスクでは、有効性をテストの Sales Employees by Territory ユーザー ロール Analyze in Excel 機能 SSDT で使用します。 EmployeeSecurity テーブルにして、ロールのメンバーとして追加したユーザー名のいずれかを指定します。 このユーザー名は、Excel とモデルの間に作成された接続で有効なユーザー名として使用されます。  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールをテストするには  
  
1.  SSDT で、**モデル** メニューをクリック**Excel で分析**します。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、 **[その他の Windows ユーザー]** をクリックし、 **[参照]** をクリックします。  
  
3.  **ユーザーまたはグループ** ダイアログ ボックスで**を選択するオブジェクト名を入力**、EmployeeSecurity テーブルに含まれるユーザー名のいずれかを入力し、クリックして**名前の確認**.  
  
4.  **[OK]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを閉じ、 **[OK]** をクリックして **[Excel で分析]** ダイアログ ボックスを閉じます。  
  
    Excel で新しいブックが開きます。 ピボット テーブルが自動的に作成されます。 ピボット テーブル フィールド リストには、ほとんど、新しいモデルで使用可能なデータ フィールドにはが含まれています。  
  
    EmployeeSecurity テーブルがピボット テーブル フィールド リストに表示されないことを確認します。 これは、前の作業でクライアント ツールからこのテーブルを非表示にすることを選択したためです。  
  
5.  **フィールド**一覧**∑ Internet Sales** (メジャー) を選択、 **InternetTotalSales**メジャーです。 メジャーは **値** フィールドに入力されます。  
  
6.  選択、 **SalesTerritoryId**列から、 **DimSalesTerritory**テーブル。 列は **行ラベル** フィールドに入力されます。  
  
    使用した有効なユーザー名が属している 1 つの地域のインターネット販売成績のみが表示されていることに注意してください。 別の列を選択した場合たとえば、市区町村、行ラベル フィールド、有効なユーザーが属する販売区域の都市のみとして DimGeography テーブルからが表示されます。  
  
    このユーザーは、自分が属する区域以外の区域のインターネット販売データを参照したり、クエリを実行することはできません。これは、Sales Employees by Territory ユーザー ロールで Sales Territory テーブルに定義された行フィルターによって、他の販売区域に関連するすべてのデータが効果的に保護されているためです。  
  
## <a name="see-also"></a>参照  
[USERNAME 関数 (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f)  
[LOOKUPVALUE 関数 (DAX)](http://msdn.microsoft.com/73a51c4d-131c-4c33-a139-b1342d10caab)  
[CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
