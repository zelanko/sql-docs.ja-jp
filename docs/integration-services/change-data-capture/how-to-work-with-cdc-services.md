---
title: "CDC サービスを操作する方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bd4d1ea9deb9451701f84470ed2f35f7aa220df2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="how-to-work-with-cdc-services"></a>CDC Service の操作方法
  この手順では、CDC Service 構成コンソールを使用して、Oracle CDC Service の操作用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備し、新しい CDC サービスを作成する方法について説明します。  
  
### <a name="to-work-with-cdc-services"></a>CDC サービスを操作するには  
  
1.  **[スタート]** メニューの **[CDC Service Configuration for Oracle]**をクリックします。  
  
2.  左ペインで **[ローカルの CDC Service]** (ルート レベル) を選択します。  
  
3.  次のいずれか、または両方のタスクを実行します。  
  
    -   **[SQL Server の準備]**  
  
         CDC Service 構成コンソールの右側にある **[アクション]** ペインで、このオプションを選択します。  
  
         **[ローカルの CDC Service]** を右クリックして **[SQLServer の準備]**をクリックすることもできます。  
  
         [Oracle CDC 用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの準備] ダイアログ ボックスが表示されます。  
  
         Oracle CDC サービス用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備するには、ログインが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定サーバー ロールを持つ `dbcreator` ログインを持っている必要があります。 このログインは、MSXDBCDC データベースの作成に使用されます。このデータベースは、Oracle CDC Service を追加する際、および後で Oracle CDC インスタンスを追加する際に必要です。  
  
         このダイアログ ボックスの使用方法の詳細については、「 [Prepare SQL Server for CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)」を参照してください。 CDC 用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを有効にする方法の詳細については、「 [CDC 用に SQL Server を準備する方法](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)」を参照してください。  
  
    -   **[新しい CDC サービスの作成]**  
  
         CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[新しいサービス]** をクリックします。  
  
         **[ローカルの CDC Service]** を右クリックして **[新しいサービス]**をクリックすることもできます。  
  
         [新しい Oracle CDC Service] ダイアログ ボックスが表示されます。  
  
         このダイアログ ボックスの使用方法の詳細については、「 [Create and Edit an Oracle CDC Service](../../integration-services/change-data-capture/create-and-edit-an-oracle-cdc-service.md)」を参照してください。 CDC サービスを作成または編集する方法の詳細については、「 [How to Create and Edit a CDC Service](../../integration-services/change-data-capture/how-to-create-and-edit-a-cdc-service.md)」を参照してください。  
  
         Oracle CDC Service によって使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは、 `public` 固定サーバー ロールのメンバーであることだけが必要です。その他の権限は必要ありません。 ただし、Oracle CDC Service を作成するには、ログインが MSXDBCDC データベースに対する書き込み権限を持っている必要があります。たとえば、ログインに **db_owner** データベース ロールが割り当てられている必要があります。 MSXDBDCDC データベースに対する書き込み権限を持たないログインが新しい Oracle CDC インスタンスの作成を試みると、エラー メッセージが表示されます。 そのダイアログ ボックスで **[OK]** をクリックします。[SQL Server への接続] ダイアログ ボックスが表示されます。  
  
         **db_owner** データベース ロールなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力する方法については、「 [Oracle CDC Service の作成と編集](../../integration-services/change-data-capture/create-and-edit-an-oracle-cdc-service.md) 」および「 [SQL Server への接続](../../integration-services/change-data-capture/connection-to-sql-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CDC Service を操作します。](../../integration-services/change-data-capture/work-with-cdc-services.md)  
  
  

