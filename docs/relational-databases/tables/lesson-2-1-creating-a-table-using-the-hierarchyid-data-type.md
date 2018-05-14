---
title: hierarchyid データ型を使用したテーブルの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a34fde9a22dd93ae67d376ca275117484adab430
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-2-1---creating-a-table-using-the-hierarchyid-data-type"></a>レッスン 2-1 - hierarchyid データ型を使用したテーブルの作成
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
EmployeeOrg という名前のテーブルを作成する例を次に示します。このテーブルには、従業員データと、それらの従業員のレポート階層が含まれています。 この例では、テーブルを [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに作成しますが、これは任意です。 例をわかりやすくするために、このテーブルには 5 つの列のみ含まれています。  
  
-   OrgNode は、階層リレーションシップを格納する **hierarchyid** 列です。  
  
-   OrgLevel は OrgNode 列に基づく計算列であり、階層内での各ノードのレベルが格納されます。 これは、幅優先のインデックスに使用されます。  
  
-   EmployeeID には、給与処理などのアプリケーションで使用される通常の従業員識別番号が含まれます。 新しいアプリケーションの開発では、アプリケーションは OrgNode 列を使用でき、この個別の EmployeeID 列は不要です。  
  
-   EmpName には、従業員の名前が含まれます。  
  
-   Title には、従業員の役職が含まれます。  
  
### <a name="to-create-the-employeeorg-table"></a>EmployeeOrg テーブルを作成するには  
  
1.  クエリ エディター ウィンドウで、次のコードを実行し、 `EmployeeOrg` テーブルを作成します。 `OrgNode` 列を、クラスター化インデックスのある主キーとして指定すると、深さ優先のインデックスが作成されます。  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  次のコードを実行して `OrgLevel` 列と `OrgNode` 列に複合インデックスを作成し、効率的な幅優先の検索をサポートします。  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
これでテーブルはデータを受け入れる準備ができました。 次に、階層的な手法を使用してテーブルにデータを入力します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[階層的な手法を使用した階層テーブルの作成](../../relational-databases/tables/lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
