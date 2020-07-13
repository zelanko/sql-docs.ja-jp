---
title: 'レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 987e6924fe3fbffb416e4266861ae7cfede16596
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108496"
---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a>レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する
  Visual C# 用の ASP.NET Web サイト テンプレートを使用して新しい Web サイト プロジェクトを作成した後は、親レポートのデータ接続とデータ テーブルを作成します。 このチュートリアルでは、データ接続先として AdventureWorks2008 データベースを使用しますが、 AdventureWorks2012 データベースに接続することもできます。  
  
### <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a>DataSet を追加してデータ接続とデータ テーブルを定義するには (親レポート用)  
  
1.  [ **Web サイト** ] メニューの [ **新しい項目の追加**] を選択します。  
  
2.  [**新しい項目の追加**] ダイアログボックスで、[**データセット**] を選択し、[**追加**] をクリックします。 メッセージが表示されたら、 **[はい]** をクリックして**App_Code**フォルダーに項目を追加する必要があります。  
  
     これにより、 **DataSet1.xsd** という新しい XSD ファイルがプロジェクトに追加され、データセット デザイナーが開きます。  
  
3.  [ツールボックス] ウィンドウから**[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** コントロールをデザイン画面にドラッグします。 これにより、 **TableAdapter** の構成ウィザードが起動します。  
  
4.  [**データ接続の選択**] ページで、[**新しい接続**] をクリックします。  
  
5.  Visual Studio で初めてデータソースを作成する場合は、 **[データソースの選択**] ページが表示されます。 **[データ ソース]** ボックスで、 **[Microsoft SQL Server]** を選択します。  
  
6.  [ **接続の追加** ] ダイアログ ボックスで、次の手順を実行します。  
  
    1.  [**サーバー名**] ボックスに、 **AdventureWorks2008**データベースが配置されているサーバーを入力します。  
  
         既定の SQL Server Express インスタンスは **(local)\sqlexpress**です。  
  
    2.  [ **サーバーへのログオン** ] セクションで、データへのアクセスを提供するオプションを選択します。 既定は **[Windows 認証を使用する]** です。  
  
    3.  [**データベース名の選択または入力**] ドロップダウンリストで、[ **AdventureWorks2008**] をクリックします。  
  
    4.  [**OK**] をクリックし、[**次へ**] をクリックします。  
  
7.  手順 6. (b) で **[SQL Server 認証を使用する]** を選択した場合は、機密データを文字列に含めるか、またはその情報をアプリケーション コードで設定するかどうかを指定するオプションを選択します。  
  
8.  [**アプリケーション構成ファイルに接続文字列を保存**] ページで、接続文字列の名前を入力するか、既定の**AdventureWorks2008ConnectionString**をそのまま使用します。 **[次へ]** をクリックします。  
  
9. [**コマンドの種類の選択**] ページで、[ **SQL ステートメントを使用する**] を選択し、[**次へ**] をクリックします。  
  
10. [ **Sql ステートメントの入力**] ページで、 **AdventureWorks2008**データベースからデータを取得するための次の transact-sql クエリを入力し、[**次へ**] をクリックします。  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
     [**クエリビルダー**] をクリックしてクエリを作成し、[**クエリの実行**] をクリックしてクエリを確認することもできます。 クエリを実行したときに期待したデータが返されない場合は、以前のバージョンの AdventureWorks を使用している可能性があります。 AdventureWorks の**AdventureWorks2008**バージョンのインストールの詳細については、「[チュートリアル: Adventureworks データベースのインストール](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)」を参照してください。  
  
11. [**生成するメソッドの選択**] ページで、[**更新を直接データベースに送信するためのメソッドを作成する (GenerateDBDirectMethods)**] チェックボックスをオフにして、[**完了**] をクリックします。  
  
    > [!WARNING]  
    >  必ずこのチェック ボックスをオフにしてください。  
  
     これで、レポートのデータ ソースとしての ADO.NET DataTable オブジェクトの構成が完了しました。 Visual Studio の [データセット デザイナー] ページに、追加した DataTable オブジェクトにクエリで指定した列が表示されます。 DataSet1 には、クエリに基づいて Product テーブルのデータが含まれています。  
  
12. ファイルを保存します。  
  
13. データをプレビューするには、[**データ**] メニューの [**データのプレビュー** ] をクリックし、[**プレビュー**] をクリックします。  
  
## <a name="next-task"></a>次の作業  
 これで、親レポートのデータ接続とデータ テーブルを作成できました。 次は、レポート ウィザードを使用して親レポートを設計します。  
  
  
