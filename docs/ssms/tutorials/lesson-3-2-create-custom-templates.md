---
title: "カスタム テンプレートの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 770b33f7fb7fa22d1a2e86d4b5c7a9d3f8c84b35
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="lesson-3-2---create-custom-templates"></a>レッスン 3-2 - カスタム テンプレートの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 一般的な作業のためのテンプレートが多数用意されていますが、テンプレートの真価は、頻繁に作成する複雑なスクリプトに適したカスタム テンプレートを作成できる点にあります。 この演習では、2 ～ 3 のパラメーターを使用した簡単なスクリプトを作成しますが、規模が大きく、反復的なスクリプトを作成する場合にもテンプレートが役立ちます。  
  
## <a name="using-custom-templates"></a>カスタム テンプレートの使用  
  
#### <a name="to-create-a-custom-template"></a>カスタム テンプレートを作成するには  
  
1.  テンプレート エクスプローラーで **[SQL Server テンプレート]**を展開します。 **[Stored Procedure]**を右クリックし、 **[新規作成]**をポイントして **[フォルダー]**をクリックします。  
  
2.  新しいテンプレート フォルダーの名前として「 **Custom** 」と入力し、Enter キーを押します。  
  
3.  **[Custom]**を右クリックし、 **[新規作成]**をポイントして **[テンプレート]**をクリックします。  
  
4.  新しいテンプレートの名前として「 **WorkOrdersProc** 」と入力し、 **Enter**キーを押します。  
  
5.  **[WorkOrdersProc]**を右クリックし、 **[編集]**をクリックします。  
  
6.  **[データベース エンジンへの接続]** ダイアログ ボックスで接続情報を確認し、 **[接続]**をクリックします。  
  
7.  クエリ エディターに次のスクリプトを入力し、特定の部分 (この例では Blade) の命令を検索するストアド プロシージャを作成します (チュートリアル ウィンドウからコードをコピーして、貼り付けることができます)。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  F5 キーを押してこのスクリプトを実行し、 **WorkOrdersForBlade** プロシージャを作成します。  
  
9. オブジェクト エクスプローラーで、**[AdventureWorks2012]** データベースを右クリックし、 **[新しいクエリ]**をクリックします。 新しいクエリ エディター ウィンドウが開きます。  
  
10. クエリ エディターに「 **EXECUTE dbo.WorkOrdersForBlade**」と入力し、F5 キーを押してクエリを実行します。 **結果**ペインに、ブレードに対する作業命令の一覧が返されていることを確認します。  
  
11. テンプレート スクリプト (手順 7 のスクリプト) を編集します。4 つの場所で、製品名 Blade をパラメーター **\<product_name, nvarchar(50), name>** に置き換えます。  
  
    > [!NOTE]  
    > パラメーターには、置き換えるパラメーターの名前、パラメーターのデータ型、パラメーターの既定値の 3 つの要素が必要です。  
  
12. スクリプトは以下のようになります。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. **[ファイル]** メニューの **[WorkOrdersProc.sql の保存]** をクリックし、テンプレートを保存します。  
  
#### <a name="to-test-the-custom-template"></a>カスタム テンプレートをテストするには  
  
1.  テンプレート エクスプローラーで **[Stored Procedure]**、 **[Custom]**の順に展開し、 **[WorkOrderProc]**をダブルクリックします。  
  
2.  **[データベース エンジンへの接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]**をクリックします。 新しいクエリ エディター ウィンドウが開き、 **WorkOrderProc** テンプレートの内容が表示されます。  
  
3.  **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]**をクリックします。  
  
4.  **[テンプレート パラメーターの値の指定]** ダイアログ ボックスで、 **product_name** の値として「 **FreeWheel** 」と入力します (既定の内容を上書きします)。次に、 **[OK]** をクリックして **[テンプレート パラメーターの値の指定]** ダイアログ ボックスを閉じ、クエリ エディターのスクリプトを更新します。  
  
5.  F5&lt;/localizedText&gt; キーを押してクエリを実行し、プロシージャを作成します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[プロジェクトまたはソリューションとしてスクリプトを保存する](../../tools/sql-server-management-studio/lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
  
