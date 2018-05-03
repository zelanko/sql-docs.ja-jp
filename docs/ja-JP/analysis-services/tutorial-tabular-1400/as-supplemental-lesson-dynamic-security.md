---
title: 'Analysis Services tutorial 補足のレッスン: 動的なセキュリティ |Microsoft ドキュメント'
description: Analysis Services チュートリアルでは行フィルターを使用して、動的なセキュリティを使用する方法について説明します。
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: ffd58456ee40741792ac7ce409c97e064a92ba43
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="supplemental-lesson---dynamic-security"></a>補足のレッスンの動的なセキュリティ

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

この補足のレッスンでは、動的なセキュリティを実装する他の役割を作成します。 動的なセキュリティには、現在ログオンしているユーザーのユーザー名またはログイン ID に基づいた行レベルのセキュリティが用意されています。 
  
動的なセキュリティを実装するのには、モデルに接続し、モデル オブジェクトとデータを参照できるユーザーのユーザー名を含む、モデルにテーブルを追加します。 このチュートリアルを使用して作成するモデルは Adventure Works; のコンテキストで、します。ただし、このレッスンを完了するには、独自のドメインのユーザーを含むテーブルを追加する必要があります。 追加されたユーザー名のパスワードが不要です。 EmployeeSecurity テーブルでは、ユーザー独自のドメインからの小さなサンプルを使用して作成するには、機能を使用する、貼り付け、Excel スプレッドシートから従業員データの貼り付けします。 実際のシナリオでは、ユーザー名を含むテーブルなりますに実際のデータベースからテーブル; データ ソースとしてたとえば、実際の DimEmployee テーブルです。  
  
動的なセキュリティを実装する 2 つの DAX 関数を使用する: [USERNAME 関数 (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f)と[LOOKUPVALUE 関数 (DAX)](http://msdn.microsoft.com/73a51c4d-131c-4c33-a139-b1342d10caab)です。 行フィルター式に適用されるこれらの関数は、新しいロールで定義されています。 LOOKUPVALUE 関数を使用すると、数式は EmployeeSecurity テーブルから値を指定します。 数式は、USERNAME 関数にログオンしたユーザーのユーザー名を指定する値がこのロールに属していることを渡します。 ユーザーは、ロールの行フィルターによって指定されたデータのみを参照できます。 このシナリオでは、営業部の従業員がメンバーとなっている販売区域のインターネット販売データをのみ参照できることを指定します。  
  
この Adventure Works テーブル モデルに固有の作業が実際のシナリオに必ずしも適用されない場合には、そのように記載されています。 各作業には、作業の目的を表す追加情報が含まれています。  
  
このレッスンの推定所要時間: **30 分**  
  
## <a name="prerequisites"></a>前提条件  

この補足のレッスン記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 この補足のレッスンの作業を実行する前に、前のレッスンをすべて完了している必要があります。  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>AW Internet Sales Tabular Model プロジェクトへの dimSalesTerritory テーブルの追加  

この Adventure Works のシナリオの動的なセキュリティを実装するのには、モデルに 2 つのテーブルを追加する必要があります。 最初に追加するテーブルは、同じ AdventureWorksDW データベース (販売区域) として DimSalesTerritory です。 後で、行フィルターは、ログオンしているユーザーが閲覧できる特定のデータを定義する SalesTerritory テーブルに適用されます。  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>dimSalesTerritory テーブルを追加するには  
  
1.  表形式モデル エクスプ ローラーで >**データソース**、接続を右クリックし、クリックして**新しいテーブルのインポート**です。  

    [権限借用の資格情報] ダイアログ ボックスが表示された場合は、「レッスン 2: データの追加」で使用した権限借用の資格情報を入力します。
  
2.  ナビゲーターの選択、 **DimSalesTerritory**テーブル、およびをクリックして**OK**です。    
  
3.  クエリ エディターで、クリックして、 **DimSalesTerritory**クエリ、および削除して**SalesTerritoryAlternateKey**列です。  
  
7.  **[インポート]** をクリックします。  
  
    新しいテーブルは、モデル ワークスペースに追加されます。 オブジェクトとソースの DimSalesTerritory テーブルからのデータは、AW Internet Sales Tabular Model にインポートされます。  
  
9. テーブルを正常にインポートした後にをクリックして**閉じる**です。  

## <a name="add-a-table-with-user-name-data"></a>ユーザー名データを含むテーブルの追加  

AdventureWorksDW サンプル データベース内の DimEmployee テーブルには、AdventureWorks ドメインのユーザーが含まれています。 それらのユーザー名は、ご使用の環境ではありません。 実際のユーザーの組織内の小さなサンプル (少なくとも 3 つ) が含まれるモデルでは、テーブルを作成する必要があります。 新しいロールにメンバーとしてこれらのユーザーを追加します。 サンプル ユーザー名、パスワード必要はありませんが、自分のドメインに実際の Windows ユーザー名は必要があります。  
  
#### <a name="to-add-an-employeesecurity-table"></a>EmployeeSecurity テーブルを追加するには  
  
1.  Microsoft Excel でワークシートを作成するを開きます。  
  
2.  ヘッダー行を含む次のテーブルをコピーし、ワークシートに貼り付けます。  

    ```
      |EmployeeId|SalesTerritoryId|FirstName|LastName|LoginId|  
      |---------------|----------------------|--------------|-------------|------------|  
      |1|2|<user first name>|<user last name>|\<domain\username>|  
      |1|3|<user first name>|<user last name>|\<domain\username>|  
      |2|4|<user first name>|<user last name>|\<domain\username>|  
      |3|5|<user first name>|<user last name>|\<domain\username>|  
    ```

3.  名前と、組織内の 3 人のユーザーのログイン id で、名、姓、名、およびドメイン \ ユーザー名を置き換えます。 EmployeeId 1 では、1 つ以上の販売区域に属しているこのユーザーを示す最初の 2 つの行に同じユーザーを配置します。 EmployeeId と SalesTerritoryId フィールドはそのままにします。  
  
4.  ワークシートとして保存**SampleEmployee**です。  
  
5.  ワークシートで、従業員に関するデータをヘッダーを含むすべてのセルを選択し、選択したデータを右クリックし、をクリックして**コピー**です。  
  
6.  SSDT をクリックして、**編集** メニューをクリックして**貼り付け**です。  
  
    貼り付けは淡色表示された場合、は、モデル デザイナー ウィンドウの任意のテーブルの任意の列をクリックしてからやり直してください。  
  
7.  **貼り付けプレビュー**ダイアログ ボックスで、**テーブル名**、型**EmployeeSecurity**です。  
  
8.  **貼り付けるデータ**データを含むすべてのユーザー データと SampleEmployee ワークシートからヘッダーを確認してください。  
  
9. **[先頭の行を列見出しとして使用する]** がオンであることを確認し、 **[OK]** をクリックします。  
  
    SampleEmployee ワークシートからコピーした従業員データを含む EmployeeSecurity をという名前の新しいテーブルが作成されます。  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成します。  

すべて FactInternetSales、DimGeography、および DimSalesTerritory テーブルには、共通の列、SalesTerritoryId が含まれています。 DimSalesTerritory テーブルの [SalesTerritoryId] 列には、販売区域ごとの別の id 値が含まれています。  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>FactInternetSales、DimGeography、および DimSalesTerritory テーブル間のリレーションシップを作成するには  
  
1.  ダイアグラム ビューでの**DimGeography**の表をクリックし、保持、 **SalesTerritoryId**列にカーソルをドラッグ、 **SalesTerritoryId**内の列、 **DimSalesTerritory**テーブル、および離します。  
  
2.  **FactInternetSales**の表をクリックし、保持、 **SalesTerritoryId**  列にカーソルをドラッグ、 **SalesTerritoryId**内の列、 **DimSalesTerritory**テーブル、および離します。  
  
    このリレーションシップのアクティブなプロパティが False で、アクティブになっていないことを確認します。 FactInternetSales テーブルには、既に別のアクティブなリレーションシップがあります。  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションから EmployeeSecurity テーブルを非表示します。  

このタスクで非表示にする、EmployeeSecurity 表に、クライアント アプリケーションのフィールド リストに表示されないようにします。 保護されませんにテーブルを非表示にすることに注意してください。 わかっている場合、ユーザーは EmployeeSecurity テーブル データを照会まだできますか。 中に、そのデータのいずれかを照会できないことを防ぐ EmployeeSecurity テーブルのデータをセキュリティで保護するには、後のタスクにフィルターを適用します。  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>クライアント アプリケーションから EmployeeSecurity テーブルを非表示にするには  
  
-   モデル デザイナーのダイアグラム ビューで、 **Employee** テーブルの見出しを右クリックし、 **[クライアント ツールで非表示にする]** をクリックします。  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールの作成  

このタスクでは、ユーザー ロールを作成します。 このロールには、定義の DimSalesTerritory テーブルのどの行がユーザーに表示された行フィルターが含まれています。 DimSalesTerritory に関連するその他のすべてのテーブルに一対多リレーションシップの方向にフィルターが適用されます。 ロールのメンバーであるすべてのユーザーがクエリ可能なされない EmployeeSecurity テーブル全体をセキュリティで保護するフィルターを適用します。  
  
> [!NOTE]  
> このレッスンで作成する Sales Employees by Territory ロールによって、メンバーが参照 (またはクエリを実行) できるデータは、自分が属する販売区域の売上データのみに制限されます。 場合は、ユーザーを追加するメンバーとして、Sales Employees by Territory ロールでロールのメンバーが作成されるようにも存在する[レッスン 11: ロールの作成](../tutorial-tabular-1400/as-lesson-11-create-roles.md)、アクセス許可の組み合わせを取得します。 あるユーザーが複数のロールのメンバーである場合、各ロールに対して定義された権限と行フィルターは累積されます。 ユーザーは、権限はロールの組み合わせによって決まります。  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールを作成するには  
  
1.  SSDT をクリックして、**モデル** メニューをクリックして**ロール**です。  
  
2.  **ロール マネージャー**をクリックして**新規**です。  
  
    "なし" 権限を設定された新しいロールがリストに追加されます。  
  
3.  [新しいロール] をクリックし、**名前**列、するロールの名前を変更**Sales Employees by Territory**です。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、 **[読み取り]** 権限を選択します。  
  
5.  クリックして、**メンバー**  タブをクリックして**追加**です。  
  
6.  **ユーザーまたはグループ**ダイアログ ボックスで、**を選択するオブジェクト名を入力**、EmployeeSecurity テーブルを作成するときに使用した最初のサンプル ユーザー名を入力します。 **[名前の確認]** をクリックしてユーザー名が有効であることを確認し、 **[OK]** をクリックします。  
  
    名前の追加の他のサンプル ユーザー EmployeeSecurity テーブルを作成するときに使用した、この手順を繰り返します。  
  
7.  クリックして、**行フィルター**タブです。  
  
8.  **EmployeeSecurity**表で、 **DAX フィルター**列で、次の数式を入力します。  
  
    ```
      =FALSE()  
    ```
  
    この数式では、すべての列が false ブール条件に解決することを指定します。 EmployeeSecurity テーブルの列が照会できるありません Sales Employees のメンバー by Territory ユーザー ロール。  
  
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

このタスクで by Territory ユーザー ロール Sales Employees の有効性をテストするのに SSDT での Excel 機能で分析を使用します。 EmployeeSecurity テーブルと、ロールのメンバーとして追加したユーザー名のいずれかを指定するとします。 このユーザー名は、Excel とモデルの間に作成した接続で有効なユーザー名として使用されます。  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Sales Employees by Territory ユーザー ロールをテストするには  
  
1.  SSDT をクリックして、**モデル** メニューをクリックして**Excel で分析**です。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、 **[その他の Windows ユーザー]** をクリックし、 **[参照]** をクリックします。  
  
3.  **ユーザーまたはグループ**ダイアログ ボックスで、**を選択するオブジェクト名を入力**EmployeeSecurity テーブルに含まれるユーザー名を入力して、をクリックして**名前の確認**です。  
  
4.  **[OK]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを閉じ、 **[OK]** をクリックして **[Excel で分析]** ダイアログ ボックスを閉じます。  
  
    Excel は、新しいブックが開きます。 ピボット テーブルが自動的に作成します。 ピボット テーブル フィールド リストには、ほとんど、新しいモデルで使用可能なデータ フィールドにはが含まれています。  
  
    EmployeeSecurity テーブルがピボット テーブル フィールド リストに表示されないことを確認します。 前のタスクでのクライアント ツールからこのテーブルを非表示します。  
  
5.  **フィールド**一覧**∑ Internet Sales** (メジャー) を選択、 **InternetTotalSales**メジャーです。 メジャーが入力されて、**値**フィールドです。  
  
6.  選択、 **SalesTerritoryId**列から、 **DimSalesTerritory**テーブル。 列が入力されて、**行ラベル**フィールドです。  
  
    使用した有効なユーザー名が属している 1 つの地域のインターネット販売成績のみが表示されていることに注意してください。 行ラベル フィールドとして DimGeography テーブルからの市区町村などの別の列を選択した場合、有効なユーザーが属する販売区域の都市のみが表示されます。  
    このユーザーは、参照または区域に属している以外の区域のすべてのインターネット販売データをクエリできません。 この制限は、DimSalesTerritory テーブルの場合、Sales Employees by Territory ユーザー ロールでは、他の販売区域に関連するすべてのデータのデータをセキュリティで保護された行フィルターが定義されているためにです。  
  
## <a name="see-also"></a>参照  

[USERNAME 関数 (DAX)](https://msdn.microsoft.com/library/hh230954.aspx)  
[LOOKUPVALUE 関数 (DAX)](https://msdn.microsoft.com/library/gg492170.aspx)  
[CUSTOMDATA 関数 (DAX)](https://msdn.microsoft.com/library/hh213140.aspx)  
