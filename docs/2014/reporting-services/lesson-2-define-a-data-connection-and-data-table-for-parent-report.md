---
title: 'レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b1fec86adc14a786d781e74f023829d81aaaf825
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179064"
---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a>レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する
  Visual C# 用の ASP.NET Web サイト テンプレートを使用して新しい Web サイト プロジェクトを作成した後は、親レポートのデータ接続とデータ テーブルを作成します。 このチュートリアルでは、データ接続先として AdventureWorks2008 データベースを使用しますが、 AdventureWorks2012 データベースに接続することもできます。  
  
### <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a>DataSet を追加してデータ接続とデータ テーブルを定義するには (親レポート用)  
  
1.  **[Web サイト]** メニューの **[新しい項目の追加]** を選択します。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、**データセット** をクリック**追加**です。 入力を求められたらする項目を追加する必要があります、 **App_Code**  をクリックしてフォルダー**はい**です。  
  
     これにより、 **DataSet1.xsd** という新しい XSD ファイルがプロジェクトに追加され、データセット デザイナーが開きます。  
  
3.  [ツールボックス] ウィンドウからドラッグして、 **[TableAdapter](http://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** コントロールをデザイン画面にします。 これにより、 **TableAdapter** の構成ウィザードが起動します。  
  
4.  **データ接続の選択**] ページで [**新しい接続**です。  
  
5.  Visual Studio で初めてデータ ソースを作成する場合は、 **[データ ソースの選択]** ページが表示されます。 **[データ ソース]** ボックスで、 **[Microsoft SQL Server]** を選択します。  
  
6.  **[接続の追加]** ダイアログ ボックスで、次の手順を実行します。  
  
    1.  **サーバー名**ボックスで、サーバー名を入力、場所、 **AdventureWorks2008**データベースがあります。  
  
         既定の SQL Server Express インスタンスは **(local)\sqlexpress**です。  
  
    2.  **[サーバーへのログオン]** セクションで、データへのアクセスを提供するオプションを選択します。 既定は **[Windows 認証を使用する]** です。  
  
    3.  **を選択するか、データベースの名前を入力**ドロップダウン リストをクリックして**AdventureWorks2008**です。  
  
    4.  **[OK]** をクリックし、 **[次へ]** をクリックします。  
  
7.  手順 6. (b) で **[SQL Server 認証を使用する]** を選択した場合は、機密データを文字列に含めるか、またはその情報をアプリケーション コードで設定するかどうかを指定するオプションを選択します。  
  
8.  **アプリケーション構成ファイルへの接続文字列を保存**ページで、接続文字列の名前を入力するか、既定の**AdventureWorks2008ConnectionString**です。 **[次へ]** をクリックします。  
  
9. **コマンドの種類を選択**] ページで、[ **SQL ステートメントの使用**、クリックして **[次へ]** です。  
  
10. **SQL ステートメントを入力** ページで、次の TRANSACT-SQL クエリからデータを取得する入力、 **AdventureWorks2008**データベース、およびをクリックして**次**です。  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
     クリックして、クエリを作成することもできます。**クエリ ビルダー**、をクリックして、クエリを確認してください**クエリの実行**です。 クエリを実行したときに期待したデータが返されない場合は、以前のバージョンの AdventureWorks を使用している可能性があります。 インストールの詳細については、 **AdventureWorks2008**のバージョンの AdventureWorks を参照してください[チュートリアル: AdventureWorks データベースのインストール](http://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)です。  
  
11. **生成するメソッドの選択** ページで、オフにしてください**更新を送信する (GenerateDBDirectMethods) データベースに直接メソッドを作成する**、クリックして**を完了**.  
  
    > [!WARNING]  
    >  必ずこのチェック ボックスをオフにしてください。  
  
     これで、レポートのデータ ソースとしての ADO.NET DataTable オブジェクトの構成が完了しました。 Visual Studio の [データセット デザイナー] ページに、追加した DataTable オブジェクトにクエリで指定した列が表示されます。 DataSet1 には、クエリに基づいて Product テーブルのデータが含まれています。  
  
12. ファイルを保存します。  
  
13. データをプレビューするには、をクリックして**データのプレビュー**上、**データ** メニューをクリックして**プレビュー**です。  
  
## <a name="next-task"></a>次の作業  
 これで、親レポートのデータ接続とデータ テーブルを作成できました。 次は、レポート ウィザードを使用して親レポートを設計します。  
  
  