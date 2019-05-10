---
title: Analysis Services チュートリアル補足のレッスン:動的なセキュリティ |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 9fbc474dbf7621b0da68edb7b310bb55ffcde7d5
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64776091"
---
# <a name="supplemental-lesson---dynamic-security"></a>補足のレッスン: 動的なセキュリティ

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

この補足のレッスンでは、動的なセキュリティを実装する追加のロールを作成します。 動的なセキュリティには、現在ログオンしているユーザーのユーザー名またはログイン ID に基づいた行レベルのセキュリティが用意されています。 
  
動的なセキュリティを実装するには、モデルに接続し、モデル オブジェクトとデータを参照できるユーザーのユーザー名を含むモデルにテーブルを追加します。 このチュートリアルを使用して作成するモデルは Adventure Works; のコンテキストで、します。ただし、このレッスンを完了するには、独自のドメインからユーザーを含むテーブルを追加する必要があります。 追加されたユーザー名のパスワードが不要です。 を独自のドメインからユーザーの小規模なサンプルでは、EmployeeSecurity テーブルを作成するには、機能を使用する、貼り付け、Excel スプレッドシートから従業員データの貼り付けします。 実際のシナリオでは、ユーザー名を含むテーブルは通常である必要の実際のデータベースのテーブルをデータ ソースとしてたとえば、実際の DimEmployee テーブルです。  
  
動的なセキュリティを実装するには、2 つの DAX 関数を使用します。[USERNAME 関数 (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f)と[LOOKUPVALUE 関数 (DAX)](http://msdn.microsoft.com/73a51c4d-131c-4c33-a139-b1342d10caab)します。 行フィルター式に適用されるこれらの関数は、新しいロールで定義されています。 LOOKUPVALUE 関数を使用すると、数式は EmployeeSecurity テーブルの値を指定します。 数式にログオンしたユーザーのユーザー名を指定する USERNAME 関数に値がこのロールに属していることを渡します。 ユーザーは、ロールの行フィルターで指定されたデータのみを参照できます。 このシナリオでは、営業部の従業員がインターネットに属している販売区域の売上データを参照できますのみを指定します。  
  
この Adventure Works テーブル モデルに固有の作業が実際のシナリオに必ずしも適用されない場合には、そのように記載されています。 各作業には、作業の目的を表す追加情報が含まれています。  
  
このレッスンを完了するまでに時間を推定するには。**30 分**  
  
## <a name="prerequisites"></a>前提条件  

この補足のレッスンの記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 この補足のレッスンの作業を実行する前に、前のレッスンをすべて完了している必要があります。  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>AW Internet Sales Tabular Model プロジェクトへの dimSalesTerritory テーブルの追加  

この Adventure Works のシナリオの動的セキュリティを実装するには、モデルに 2 つのテーブルを追加する必要があります。 最初に追加するテーブルは、同じ AdventureWorksDW データベースからの (販売区域) として DimSalesTerritory です。 後で、ログオン ユーザーが参照できる特定のデータを定義する、SalesTerritory テーブルに行フィルターを適用します。  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>dimSalesTerritory テーブルを追加するには  
  
1.  表形式モデル エクスプ ローラーで >**データソース**、接続を右クリックし、クリックして**新しいテーブルのインポート**します。  

    レッスン 2 で使用した場合、ダイアログ ボックスが表示されたら、権限借用の資格情報は、権限借用の資格情報を入力します。データを追加します。
  
2.  ナビゲーターで、選択、 **DimSalesTerritory**テーブル、およびクリックして **[ok]**。    
  
3.  クエリ エディターで、クリックして、 **DimSalesTerritory**クエリ、および削除し、 **SalesTerritoryAlternateKey**列。  
  
7.  **[インポート]** をクリックします。  
  
    新しいテーブルは、モデル ワークスペースに追加されます。 オブジェクトおよびデータ ソースの DimSalesTerritory テーブルは、し、AW Internet Sales Tabular Model にインポートされます。  
  
9. テーブルが正常にインポートされたら、クリックして**閉じる**します。  

## <a name="add-a-table-with-user-name-data"></a>ユーザー名データを含むテーブルの追加  

AdventureWorksDW サンプル データベース内の DimEmployee テーブルには、AdventureWorks ドメインのユーザーが含まれています。 これらのユーザー名は、独自の環境ではありません。 実際のユーザーの組織からの小さなサンプル (少なくとも 3 つ) を含む、モデルでは、テーブルを作成する必要があります。 新しいロールにメンバーとしてこれらのユーザーを追加します。 サンプル ユーザー名、パスワード必要はありませんが、独自のドメインからの実際の Windows ユーザー名が必要です。  
  
#### <a name="to-add-an-employeesecurity-table"></a>EmployeeSecurity テーブルを追加するには  
  
1.  ワークシートを作成する、Microsoft Excel を開きます。  
  
2.  ヘッダー行を含む次のテーブルをコピーし、ワークシートに貼り付けます。  

    ```
      |EmployeeId|SalesTerritoryId|FirstName|LastName|LoginId|  
      |---------------|----------------------|--------------|-------------|------------|  
      |1|2|<user first name>|<user last name>|\<domain\username>|  
      |1|3|<user first name>|<user last name>|\<domain\username>|  
      |2|4|<user first name>|<user last name>|\<domain\username>|  
      |3|5|<user first name>|<user last name>|\<domain\username>|  
    ```

3.  名前と、組織内の 3 つのユーザーのログイン id では、名、姓、名、および domain \username を置き換えます。 同じユーザーを EmployeeId 1 の最初の 2 つの行を配置、このユーザーを示す 1 つ以上の販売区域に属しています。 そのまま、EmployeeId と SalesTerritoryId フィールド。  
  
4.  ワークシートとして保存**SampleEmployee**します。  
  
5.  ワークシートでヘッダーを含む、従業員データを含むすべてのセルを選択し、選択したデータを右クリックし、順にクリックします**コピー**します。  
  
6.  SSDT で、**編集** メニューをクリック**貼り付け**します。  
  
    貼り付けがグレーの場合、モデル デザイナー ウィンドウで任意のテーブルの任意の列をクリックします。 もう一度やり直してください。  
  
7.  **貼り付けプレビュー**  ダイアログ ボックスで**テーブル名**、型**EmployeeSecurity**します。  
  
8.  **貼り付けるデータ**データには、すべてのユーザー データと SampleEmployee ワークシートからヘッダーが含まれます。 ことを確認します。  
  
9. **[先頭の行を列見出しとして使用する]** がオンであることを確認し、 **[OK]** をクリックします。  
  
    SampleEmployee ワークシートからコピーした従業員データを含む、EmployeeSecurity という名前の新しいテーブルが作成されます。  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成します。  

FactInternetSales、DimGeography、および DimSalesTerritory テーブルすべてでは、共通の列、SalesTerritoryId を含みます。 DimSalesTerritory テーブルの SalesTerritoryId 列には、販売区域ごとのさまざまな Id 値が含まれています。  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成するには  
  
1.  ダイアグラム ビューでの**DimGeography**テーブルをクリックして、保持、 **SalesTerritoryId**列にカーソルをドラッグし、 **SalesTerritoryId** 内の列**DimSalesTerritory**テーブル、および離します。  
  
2.  **FactInternetSales**テーブルをクリックして、保持、 **SalesTerritoryId**  列にカーソルをドラッグし、 **SalesTerritoryId**内の列、 **DimSalesTerritory**テーブル、および離します。  
  
    このリレーションシップの Active プロパティが False で、アクティブになっていないことを確認します。 FactInternetSales テーブルが既に別のアクティブなリレーションシップを使用しています。  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションで EmployeeSecurity テーブルを非表示にします。  

このタスクで非表示にする、EmployeeSecurity テーブルでは、クライアント アプリケーションのフィールド リストに表示されないようにします。 テーブルを非表示を保護しませんに留意してください。 わかっている場合、ユーザーは EmployeeSecurity テーブル データをクエリでもできますか。 ユーザーに対して、そのデータのクエリを実行できることができないように、EmployeeSecurity テーブル データをセキュリティで保護するには、後のタスクでのフィルターが適用されます。  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションで EmployeeSecurity テーブルを非表示にするには  
  
-   モデル デザイナーのダイアグラム ビューで、 **Employee** テーブルの見出しを右クリックし、 **[クライアント ツールで非表示にする]** をクリックします。  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールの作成  

このタスクでは、ユーザー ロールを作成します。 このロールには、DimSalesTerritory テーブルの行がユーザーに表示を定義する行フィルターが含まれます。 DimSalesTerritory に関連するその他のすべてのテーブルと一対多リレーションシップの方向にフィルターが適用されます。 任意のユーザー ロールのメンバーであるクエリを実行できる EmployeeSecurity テーブル全体をセキュリティで保護するフィルターが適用されます。  
  
> [!NOTE]  
> このレッスンで作成する Sales Employees by Territory ロールによって、メンバーが参照 (またはクエリを実行) できるデータは、自分が属する販売区域の売上データのみに制限されます。 追加する場合、ユーザーをメンバーとして、Sales Employees by Territory ロールで作成したロールのメンバーにも存在する[レッスン 11。ロールを作成](../tutorial-tabular-1400/as-lesson-11-create-roles.md)、アクセス許可の組み合わせを取得します。 あるユーザーが複数のロールのメンバーである場合、各ロールに対して定義された権限と行フィルターは累積されます。 これは、ユーザーに権限のロールの組み合わせによって決まります。  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールを作成するには  
  
1.  SSDT で、**モデル** メニューをクリック**ロール**します。  
  
2.  **ロール マネージャー**、 をクリックして**新規**します。  
  
    "なし" 権限を設定された新しいロールがリストに追加されます。  
  
3.  新しいロールをクリックし、**名前** 列にロールの名前を変更**Sales Employees by Territory**。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、 **[読み取り]** 権限を選択します。  
  
5.  をクリックして、**メンバー**タブをクリックし、をクリックし、**追加**します。  
  
6.  **[ユーザーまたはグループ**] ダイアログ ボックスで**を選択するオブジェクト名を入力します。**、EmployeeSecurity テーブルを作成するときに使用した最初のサンプル ユーザー名を入力します。 **[名前の確認]** をクリックしてユーザー名が有効であることを確認し、 **[OK]** をクリックします。  
  
    その他のサンプル ユーザー名を追加、EmployeeSecurity テーブルの作成時に使用した、この手順を繰り返します。  
  
7.  をクリックして、**行フィルター**タブ。  
  
8.  **EmployeeSecurity**表で、 **DAX フィルター**列で、次の数式を入力します。  
  
    ```
      =FALSE()  
    ```
  
    この数式では、すべての列が false ブール条件に解決されることを指定します。 EmployeeSecurity テーブルの列は照会できません Sales Employees のメンバー by Territory ユーザー ロール。  
  
9. **DimSalesTerritory**テーブルで、次の数式を入力します。  

    ```  
    ='DimSalesTerritory'[SalesTerritoryKey]=LOOKUPVALUE('EmployeeSecurity'[SalesTerritoryId], 
      'EmployeeSecurity'[LoginId], USERNAME(), 
      'EmployeeSecurity'[SalesTerritoryId], 'DimSalesTerritory'[SalesTerritoryKey]) 
    ```
  
    この数式では、LOOKUPVALUE 関数は、EmployeeSecurity [LoginId] 現在ログオンしている Windows ユーザー名と同じであり、EmployeeSecurity [SalesTerritoryId] が DimEmployeeSecurity [SalesTerritoryId] 列のすべての値を返します、。DimSalesTerritory [SalesTerritoryId] と同じです。  
  
    LOOKUPVALUE によって返された Id の販売区域のセットは、DimSalesTerritory テーブルに表示される行を制限する、使用されます。 行の SalesTerritoryID が LOOKUPVALUE 関数によって返される id セット内にある行のみが表示されます。  
  
10. ロール マネージャー をクリックして**Ok**します。  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールのテスト  

このタスクでは、有効性をテストの Sales Employees by Territory ユーザー ロール SSDT での Excel 機能で分析を使用します。 EmployeeSecurity テーブルにして、ロールのメンバーとして追加したユーザー名のいずれかを指定します。 このユーザー名は、Excel とモデルの間に作成された接続で有効なユーザー名として使用し、されます。  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールをテストするには  
  
1.  SSDT で、**モデル** メニューをクリック**Excel で分析**します。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、 **[その他の Windows ユーザー]** をクリックし、 **[参照]** をクリックします。  
  
3.  **ユーザーまたはグループ** ダイアログ ボックスで**を選択するオブジェクト名を入力**、EmployeeSecurity テーブルに含まれるユーザー名を入力し、クリックして**名前の確認**します。  
  
4.  **[OK]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを閉じ、 **[OK]** をクリックして **[Excel で分析]** ダイアログ ボックスを閉じます。  
  
    Excel は、新しいブックを開きます。 ピボット テーブルが自動的に作成されます。 ピボット テーブル フィールド リストには、ほとんど、新しいモデルで使用可能なデータ フィールドにはが含まれています。  
  
    EmployeeSecurity テーブルがピボット テーブル フィールド リストに表示されないことを確認します。 このテーブルを前の作業でクライアント ツールから非表示にしました。  
  
5.  **フィールド**一覧**∑ Internet Sales** (メジャー) を選択、 **InternetTotalSales**メジャーです。 メジャーが入力された、**値**フィールド。  
  
6.  選択、 **SalesTerritoryId**列から、 **DimSalesTerritory**テーブル。 列が入力された、**行ラベル**フィールド。  
  
    使用した有効なユーザー名が属している 1 つの地域のインターネット販売成績のみが表示されていることに注意してください。 行ラベル フィールドとして DimGeography テーブルの City など、別の列を選択した場合、有効なユーザーが属する販売区域の都市のみが表示されます。  
    このユーザーは、参照または区域に属している以外の区域のインターネット販売データをクエリできません。 この制限は、Sales Employees by Territory ユーザー ロールで DimSalesTerritory テーブルに、他の販売区域に関連するすべてのデータの保護行フィルターが定義されているためにです。  
  
## <a name="see-also"></a>参照  

[USERNAME Function (DAX)](https://msdn.microsoft.com/library/hh230954.aspx)  
[LOOKUPVALUE Function (DAX)](https://msdn.microsoft.com/library/gg492170.aspx)  
[CUSTOMDATA 関数 (DAX)](https://msdn.microsoft.com/library/hh213140.aspx)  
