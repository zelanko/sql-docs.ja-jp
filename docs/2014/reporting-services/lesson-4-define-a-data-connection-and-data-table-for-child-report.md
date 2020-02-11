---
title: 'レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1008202519f1d9bcbf48dfdc4cd4ef3a3cbbe20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108471"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a>レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する
  親レポートを設計した後は、子レポートのデータ接続とデータ テーブルを作成します。 このチュートリアルでは、データ接続先として AdventureWorks2008 データベースを使用しますが、 AdventureWorks2012 データベースに接続することもできます。  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a>DataSet を追加してデータ接続と DataTable を定義するには (子レポート用)  
  
1.  [ **Web サイト**] メニューの [**新しい項目の追加**] をクリックします。  
  
2.  [**新しい項目の追加**] ダイアログボックスで、[**データセット**] をクリックし、[**追加**] をクリックします。 メッセージが表示されたら、 **[はい]** をクリックして**App_Code**フォルダーに項目を追加します。  
  
     これにより、 **DataSet2.xsd** という新しい XSD ファイルがプロジェクトに追加され、データセット デザイナーが開きます。  
  
3.  [ツールボックス] ウィンドウから **TableAdapter** コントロールをデザイン画面にドラッグします。 これにより、 **TableAdapter** の構成ウィザードが起動します。  
  
4.  [**データ接続の選択**] ページで、[**新しい接続**] をクリックします。  
  
5.  **[接続の追加]** ダイアログ ボックスで、次の手順を実行します。  
  
    1.  [**サーバー名**] ボックスに、 **AdventureWorks2008**データベースが配置されているサーバーを入力します。  
  
         既定の SQL Server Express インスタンスは **(local)\sqlexpress**です。  
  
    2.  **[サーバーへのログオン]** セクションで、データへのアクセスを提供するオプションを選択します。 既定は **[Windows 認証を使用する]** です。  
  
    3.  [**データベース名の選択または入力**] ドロップダウンリストで、[ **AdventureWorks2008**] をクリックします。  
  
    4.  [**OK**] をクリックし、[**次へ**] をクリックします。  
  
6.  手順 5. (b) で [ **SQL Server 認証を使用する** ] を選択した場合は、機密データを文字列に含めるか、またはその情報をアプリケーション コードで設定するかどうかを指定するオプションを選択します。  
  
7.  [**アプリケーション構成ファイルに接続文字列を保存**] ページで、接続文字列の名前を入力するか、既定の**AdventureWorks2008ConnectionString**をそのまま使用します。 **[次へ]** をクリックします。  
  
8.  [**コマンドの種類の選択**] ページで、[ **SQL ステートメントを使用する**] を選択し、[**次へ**] をクリックします。  
  
9. [ **Sql ステートメントの入力**] ページで、 **AdventureWorks2008**データベースからデータを取得するための次の transact-sql クエリを入力し、[**次へ**] をクリックします。  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
     また、[**クエリビルダー**] をクリックしてクエリを作成し、[クエリの**実行**] ボタンをクリックしてクエリを確認することもできます。 クエリを実行したときに期待したデータが返されない場合は、以前のバージョンの AdventureWorks を使用している可能性があります。 AdventureWorks の**AdventureWorks2008**バージョンのインストールの詳細については、「[チュートリアル: Adventureworks データベースのインストール](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)」を参照してください。  
  
10. [**生成するメソッドの選択**] ページで、[**更新を直接データベースに送信するためのメソッドを作成する (GenerateDBDirectMethods)**] チェックボックスをオフにし、[**完了**] をクリックします。  
  
     これで、レポートのデータソースとしての ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx)の構成が完了しました。 Visual Studio の [データセット デザイナー] ページに、追加した **DataTable** にクエリで指定した列が表示されます。 DataSet2 には、クエリに基づいて PurhcaseOrderDetail テーブルのデータが含まれています。  
  
11. ファイルを保存します。  
  
12. データをプレビューするには、[**データ**] メニューの [**データのプレビュー** ] をクリックし、[**プレビュー**] をクリックします。  
  
## <a name="next-task"></a>次の作業  
 これで、子レポートのデータ接続とデータ テーブルを作成できました。 次は、レポート ウィザードを使用して子レポートを設計します。  
  
  
