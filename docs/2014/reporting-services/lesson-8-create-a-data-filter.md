---
title: 'レッスン 8: データ フィルターを作成する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5204cab43e3c801acf80113ec92c51e00c0f9d13
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108388"
---
# <a name="lesson-8-create-a-data-filter"></a>レッスン 8: データ フィルターを作成する
  親レポートにドリルスルー アクションを追加した後は、子レポート用に定義したデータ テーブル用のデータ フィルターを作成します。  
  
 詳細レポートに対しては、テーブルベースのフィルター **または** クエリ フィルターを作成できます。 このレッスンでは、両方のオプションの手順を説明します。  
  
## <a name="table-based-filter"></a>テーブルベースのフィルター  
 テーブルベースのフィルターを実装するには、次の操作を実行する必要があります。  
  
-   子レポートの Tablix にフィルター式を追加します。  
  
-   
  `PurchaseOrderDetail` テーブルからフィルター選択されていないデータを選択する関数を作成します。  
  
-   子レポートに `PurchaseOrderDetail` DataTable をバインドするイベント ハンドラーを追加します。  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a>子レポートの Tablix にフィルター式を追加するには  
  
1.  子レポートを開きます。  
  
2.  Tablix の列見出しを選択し、列見出しの上に表示されている灰色のセルを右クリックして、[ **tablix のプロパティ**] をクリックします。  
  
3.  [**フィルター** ] ページをクリックし、[**追加**] をクリックします。  
  
4.  [**式**] フィールドで、 `ProductID`ドロップダウンリストからをクリックします。 これは、フィルターを適用する列です。  
  
5.  [演算子] ボックス**=** の一覧で、 **** 等号 () 演算子をクリックします。  
  
6.  [**値**] フィールドの横にある式ボタンをクリックし、 **[カテゴリ**] 領域の [**パラメーター** ] `productid`をクリックして、[**値**] 領域内をダブルクリックします。 **[式の設定: 値]** フィールドに、 **=Parameters!productid.Value**のような式が表示されます。  
  
7.  [ **Ok] を**クリックし、[ **Tablix のプロパティ**] ダイアログボックスでもう一度 [ **ok]** をクリックします。  
  
8.  .rdlc ファイルを保存します。  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a>PurchaseOrderDetail テーブルからフィルター選択されていないデータを選択する関数を作成するには  
  
1.  ソリューション エクスプローラーで、Default.aspx を展開し、Default.aspx.cs をダブルクリックします。  
  
2.  Integer 型のパラメーター `productid`を受け取り、 `datatable`オブジェクトを返す新しい関数を作成し、次のようにします。  
  
    1.  「 `DataSet2`[レッスン 4: 子レポートのデータ接続とデータテーブルを定義する](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)」の手順2で作成したデータセットのインスタンスを作成します。  
  
    2.  SqlServer データベースへの接続を作成し、 **「レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する」** で定義されたクエリを実行します。  
  
    3.  クエリにより、フィルター選択されていないデータが返されます。  
  
    4.  クエリを実行して、フィルター選択されていないデータを DataSet インスタンスに入力します。  
  
    5.  
  `PurchaseOrderDetail` DataTable を返します。  
  
         関数は次のようになります (これは単なる参考です。 任意のパターンに従って、子レポートに必要なデータをフェッチできます)。  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a>子レポートに PurchaseOrderDetail DataTable をバインドするイベント ハンドラーを追加するには  
  
1.  Default.aspx を開きます。  
  
2.  ReportViewer コントロールを右クリックし、[プロパティ] をクリックし**ます。**  
  
3.  [**プロパティ**] ページで、[**イベント**] アイコンをクリックします。  
  
4.  [**ドリルスルー** ] イベントをダブルクリックします。  
  
     次に示すブロックに似たイベント ハンドラー セクションがコードに追加されます。  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  イベント ハンドラーを完成させます。 このイベント ハンドラーには、次の機能を含めます。  
  
    1.  *DrillthroughEventArgs* パラメーターから子レポート オブジェクト参照をフェッチする。  
  
    2.  関数を呼び出します。`GetPurchaseOrderDetail`  
  
    3.  
  `PurchaseOrderDetail` DataTable をレポートの対応するデータ ソースにバインドする。  
  
         完成したイベント ハンドラーのコードは、次のようになります。  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  ファイルを保存します。  
  
## <a name="query-filter"></a>クエリ フィルター  
 クエリ フィルターを実装するには、次の操作を実行する必要があります。  
  
-   
  `PurchaseOrderDetail` テーブルからフィルター選択されたデータを選択する関数を作成します。  
  
-   パラメーター値を取得し、その`PurchaseOrdeDetail` DataTable を子レポートにバインドするイベントハンドラーを追加します。  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a>PurchaseOrderDetail テーブルからフィルター選択されたデータを選択する関数を作成するには  
  
1.  ソリューション エクスプローラーで、Default.aspx を展開し、Default.aspx.cs をダブルクリックします。  
  
2.  新しい関数を作成します。この関数は、Integer 型の `productid` パラメーターを受け取った後、`datatable` オブジェクトを返し、次の操作を行います。  
  
    1.  「 `DataSet2`[レッスン 4: 子レポートのデータ接続とデータテーブルを定義する](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)」の手順2で作成したデータセットのインスタンスを作成します。  
  
    2.  SqlServer データベースへの接続を作成し、 **「レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する」** で定義したクエリを実行します。  
  
    3.  このクエリには、返されるデータを親レポートで選択された `productid` に基づいてフィルター選択するための `ProductID` パラメーターが含まれます。  
  
    4.  クエリを実行して、フィルター選択されたデータを DataSet インスタンスに入力します。  
  
    5.  
  `PurchaseOrderDetail` DataTable を返します。  
  
         関数は次のようになります (これは単なる参考です。 任意のパターンに従って、子レポートに必要なデータをフェッチできます)。  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a>パラメーター値を取得し、PurchaseOrderDetail DataTable を子レポートにバインドするイベント ハンドラーを追加するには  
  
1.  Default.aspx を開きます。  
  
2.  ReportViewer コントロールを右クリックし、[**プロパティ**] をクリックします。  
  
3.  [**プロパティ**] ウィンドウで、[**イベント**] アイコンをクリックします。  
  
4.  [**ドリルスルー** ] イベントをダブルクリックします。  
  
     次のようなイベント ハンドラー セクションがコードに追加されます。  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  イベント ハンドラーを完成させます。 このイベント ハンドラーには、次の機能を含めます。  
  
    1.  *DrillthroughEventArgs* パラメーターから子レポート オブジェクト参照をフェッチする。  
  
    2.  フェッチした子レポート オブジェクトから子レポート パラメーター リストを取得する。  
  
    3.  パラメーターのコレクションに対して反復処理を行い、親レポートから渡された `ProductID` パラメーターの値を取得する。  
  
    4.  
  `GetPurchaseOrderDetail` 関数を呼び出し、`ProductID` パラメーターの値を渡す。  
  
    5.  `PurchaseOrderDetail` DataTable をレポートの対応するデータソースにバインドします。  
  
         完成したイベント ハンドラーのコードは、次のようになります。  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  ファイルを保存します。  
  
## <a name="next-task"></a>次の作業  
 これで、子レポートに対して定義したデータ テーブルのデータ フィルターを作成できました。 次は、Web サイト アプリケーションをビルドして実行します。  
  
  
